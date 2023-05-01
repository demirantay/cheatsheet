# Query Errors

Please help me fix the queries down below for their intended output:

## Total Students By Date

```python
"SELECT COUNT(*) AS EACH_DAY_TOTAL, substr(created_at, 1, 10) AS DATE FROM students WHERE (created_at BETWEEN '" + min_date + " 00:00:00' AND '" + \
                    max_date + \
                    " 23:59:59') AND deleted_at IS NULL AND account_id = 1 AND branch_id = 1 GROUP BY DATE(created_at)"
```

- If `min_date` is 02/04/2022 (mm-dd-yy) and `max_date` is 02/11/2022 -- the output will be `421`
- If `min_date` is 08/28/2022 (mm-dd-yy) and `max_date` is 08/27/2023 -- the output will be `NULL` 

## Total Quotes By Date

```python

"""
                SELECT COUNT(*) AS EACH_DAY_TOTAL, substr(created_at, 1, 10) AS DATE
                FROM quotes
                WHERE (created_at between '""" + min_date + """ 00:00:00' and '""" + max_date + """ 23:59:59')
                  AND account_id = 1
                  AND branch_id = 1
                GROUP BY DATE(created_at)
"""

```

- If `min_date` is 02/04/2022 (mm-dd-yy) and `max_date` is 02/11/2022 -- the output will be `715`
- If `min_date` is 08/28/2022 (mm-dd-yy) and `max_date` is 08/27/2023 -- the output will be `NULL` 

## Total Invoices By Date

```python
"SELECT COUNT(*) AS EACH_DAY_TOTAL, substr(created_at, 1, 10) AS DATE FROM invoices as i WHERE (created_at BETWEEN '" + min_date + " 00:00:00' AND '" + \
                    max_date + \
                    " 23:59:59') AND account_id = 1 AND branch_id = 1 AND i.invoice_is_canceled != 1 GROUP BY DATE(created_at)"
```

- If `min_date` is 02/04/2022 (mm-dd-yy) and `max_date` is 02/11/2022 -- the output will be `66`
- If `min_date` is 08/28/2022 (mm-dd-yy) and `max_date` is 08/27/2023 -- the output will be `NULL` 

## Total Sales By Date

```python
select SUM(price) as TOTAL from `invoices` inner join `students` on `students`.`student_id` = `invoices`.`student_id` where (`invoices`.`issue_date` >= '" + \
                    min_date + "' and `invoices`.`issue_date` <= '" + max_date + \
                    "') and invoice_is_canceled != 1
                
```

- If `min_date` is 02/04/2022 (mm-dd-yy) and `max_date` is 02/11/2022 -- the output will be `300.000`
- If `min_date` is 08/28/2022 (mm-dd-yy) and `max_date` is 08/27/2023 -- the output will be `NULL` 


## Daily Availability

Current SQL Query:
```sql
SELECT COUNT(pccr.room_id)            AS TotalRooms,
                   curdate()                      as todays_date,
                   (SELECT COUNT(room_id)
                    FROM invoices_courses_placements
                    WHERE placement_start = curdate()
                   )                              AS BookedRooms,
                   COUNT(pccr.room_id) - (SELECT COUNT(room_id)
                                          FROM invoices_courses_placements
                                          WHERE placement_start = curdate())
                                                  AS AvailableRooms,
                   (COUNT(pccr.room_id) - (SELECT COUNT(room_id)
                                           FROM invoices_courses_placements
                                           WHERE placement_start = curdate()
                   )) / COUNT(pccr.room_id) * 100 AS Available,
                   ((SELECT COUNT(room_id)
                     FROM invoices_courses_placements
                     WHERE placement_start = curdate()
                   )) / COUNT(pccr.room_id) * 100 AS Booked
            FROM partners_campuses_courses_rooms AS pccr
                     JOIN partners_campuses_courses pcc on pccr.course_id = pcc.course_id
                     JOIN partners_campuses pc on pcc.campus_id = pc.campus_id
                     JOIN partners p on pc.partner_id = p.partner_id
            WHERE (pccr.deleted_at IS NULL OR pccr.deleted_at >= curdate())
              AND (pcc.deleted_at IS NULL)
              AND pcc.course_status = 1
              AND pc.is_online_booking = 1
              AND pc.campus_status = 1
              AND pccr.start <= curdate()
              AND pccr.end >= curdate()
              AND p.deleted_at IS NULL
              and pccr.deleted_at is null
              AND pcc.deleted_at IS NULL
              AND pccr.room_id NOT IN (SELECT room_id
                                       FROM partners_campuses_courses_rooms_holds AS holds
                                       WHERE holds.hold_start <= curdate()
                                         AND curdate() <= holds.hold_end)
              AND pccr.room_id NOT IN (SELECT room_id
                                       FROM partners_campuses_courses_rooms_stops AS stops
                                       WHERE stops.stop_start <= curdate()
                                         AND curdate() <= stops.stop_end);
```
Current output: 
```javascript
{
  "TotalRooms": 817, 
  "todays_date": "2022-02-11", 
  "BookedRooms": 812, 
  "AvailableRooms": 5, 
  "Available": 0.612, 
  "Booked": 99.388
}
```

## Sellable Loss Weeks

---


## Cancellations

API Endpoint Query
```python
@csrf_exempt
def CRMCancelation2(request, min_date, max_date):
    cancelation_invoices_query = """SELECT s.student_id,ic.invoice_id, a.name,price,paid,IFNULL(deposit_amount, 0) as deposit_amount,deposit_paid_amount, s.student_name, invoice_cancel_reason
FROM invoices
     JOIN admins a on invoices.admin_id = a.id
     JOIN students s on invoices.student_id = s.student_id
     JOIN invoices_courses ic on invoices.invoice_id = ic.invoice_id
WHERE invoice_is_canceled = 1
AND ((ic.invoice_course_start_date between'""" + min_date + """' and '""" + max_date + """')
AND (ic.invoice_course_end_date between'""" + min_date + """' and '""" + max_date + """'))
GROUP BY s.student_id
ORDER BY ic.invoice_course_start_date DESC"""
    cancelation_invoices = pd.read_sql(cancelation_invoices_query, con=db_connection)
    cancelation_invoices_result = cancelation_invoices.to_dict('records')
    cancelation_invoices_byadmins_query = """SELECT a.name, count(*) as total
FROM invoices
     JOIN admins a on invoices.admin_id = a.id
     JOIN students s on invoices.student_id = s.student_id
     JOIN invoices_courses ic on invoices.invoice_id = ic.invoice_id
WHERE invoice_is_canceled = 1
AND ((ic.invoice_course_start_date between'""" + min_date + """' and '""" + max_date + """')
AND (ic.invoice_course_end_date between'""" + min_date + """' and '""" + max_date + """'))
GROUP BY a.name
ORDER BY total DESC"""

    cancelation_invoices_byadmins = pd.read_sql(cancelation_invoices_byadmins_query, con=db_connection)
    cancelation_invoices_byadmins_result = cancelation_invoices_byadmins.to_dict('records')

    total_invoices_query = """SELECT a.name, count(*) as total
FROM invoices
     JOIN admins a on invoices.admin_id = a.id
     JOIN students s on invoices.student_id = s.student_id
     JOIN invoices_courses ic on invoices.invoice_id = ic.invoice_id
WHERE ((ic.invoice_course_start_date between '""" + min_date + """' and '""" + max_date + """')
AND (ic.invoice_course_end_date between '""" + min_date + """' and '""" + max_date + """'))
GROUP BY a.name
ORDER BY total DESC"""

    total_invoices = pd.read_sql(total_invoices_query, con=db_connection)
    total_invoices_result = total_invoices.to_dict('records')

    cancelation_ratio = []
    for i in cancelation_invoices_byadmins_result:
        obj = {
            'name': i['name'],
            'ratio': 0
        }
        for j in total_invoices_result:
            if i['name'] == j['name']:
                obj['ratio'] = round(i['total'] / j['total'] * 100, 1)
                cancelation_ratio.append(obj)
    result = {
        'cancelation_ratio': cancelation_ratio,
        'cancelation_invoice': cancelation_invoices_result
    }
    response = JsonResponse(result, safe=False)
    return response
```

Response for `londonist_dmc/crm/cancelations_2/2022-01-17/2022-02-14/`:
```javascript
{
  "cancelation_ratio": [
    {
      "name": "Arda Celebi",
      "ratio": 33.3
    }
  ],
  "cancelation_invoice": [
    {
      "student_id": 70894,
      "invoice_id": 11825,
      "name": "Arda Celebi",
      "price": 0.0,
      "paid": 0.0,
      "deposit_amount": 0.0,
      "deposit_paid_amount": 0.0,
      "student_name": "Sera Canbaz",
      "invoice_cancel_reason": null
    }
  ]
}
```
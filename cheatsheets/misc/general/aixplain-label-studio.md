# Label Studio

## Label Studio Terms

|Term|Description|
|--|--|
|`Dataset`|What you import into Label Studio, comprised of individual items, or labeling tasks.|
| `Task` | A distinct item from a dataset that is ready to be labeled, pre-annotated, or has already been annotated. For example: a sentence of text, an image, or a video clip. |
| `Region` | The portion of the task identified for labeling. For images, an example region is a bounding box. For text, an example region is a span of text. Often has a label assigned to it. |
| `Labels` | What you add to each region while labeling a task in Label Studio. |
| `Relation` | A defined relationship between two labeled regions. |
| `Result` | A label applied to a specific region as stored in an annotation or prediction. See Label Studio JSON format of annotated tasks. |
| `Predictions` | What machine learning models create for an unlabeled dataset. |
| `Pre-annotations` | 	Predicted annotations in Label Studio format, either in a file or from a machine learning backend. See import pre-annotations. |
| `Annotations` | The output of a labeling task. Previously called “completions”. |
| `Templates` | Example labeling configurations that you can use to specify the type of labeling that you’re performing with your dataset. See all available templates |
| `Tags` | Configuration options to customize the labeling interface. See more about tags. |
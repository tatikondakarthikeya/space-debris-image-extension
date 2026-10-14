# Dataset setup and provenance

No dataset is included in this repository.

Before running the notebook, record the dataset's exact title, original source URL, version/download date, citation, and license/terms here. Verify that redistribution of images and annotations is permitted before adding any data to Git.

Expected directory layout in the current notebook:

```text
<dataset-root>/
  train/images/
  train/labels/
  valid/images/
  valid/labels/
```

The current notebook assumes `.jpg` image filenames and manually defines the class mapping as `debris` and `satellite`; verify both against the actual dataset. Its `/kaggle/input/...` path must be changed for non-Kaggle environments.

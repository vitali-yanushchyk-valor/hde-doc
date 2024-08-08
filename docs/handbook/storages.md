---
layout: default
title: Storages
nav_order: 2
---


### Service Overview
The service utilizes three Azure containers for different types of data and functionality:

- **AZURE_CONTAINER_HDE**: This is a writable container used for storing encodings data.
- **AZURE_CONTAINER_HOPE**: A read-only container that stores images from the HOPE dataset.
- **AZURE_CONTAINER_DNN**: A read-only container containing DNN files, specifically deploy.prototxt and res10_300x300_ssd_iter_140000.caffemodel.
DNN File Management

Depending on the **constance.config.DNN_FILES_SOURCE** setting, the service fetches DNN files from either GitHub or AZURE_CONTAINER_DNN using a Celery task. At startup, if local DNN files are absent, an automatic download is triggered. For manual updates and interventions, access is provided through the admin panel at: **Home › Faces › DNN files**.

### File Storage and Accessibility
Downloaded files are stored in the **settings.CV2DNN_DIR** folder. This directory must be accessible to both the backend services and Celery workers to ensure proper operation.

### Future Updates
In the future, the files within **AZURE_CONTAINER_DNN** can be automatically updated with new versions of the trained model via a dedicated pipeline, ensuring the service always uses the most current model for face recognition tasks.

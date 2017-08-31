# Steps to upload the model in GCloud ML 

- create the bucket 
    gsutil mb -l europe-west1 gs://keras-class-vitojph

- copy the exported model into the bucket 

    gsutil cp -R exported_model/* gs://keras-class-vitojph/earnings_v1

- create the model (crappy name because the evident name was used in a previous course)

    gcloud ml-engine models create keras_earnings --regions europe-west1

- create the v1 of your model

    glcoud ml-engine versions create v1 --model=keras_earnings --origin=gs://keras-class-vitojph/earnings_v1

- predict only

    gcloud ml-engine predict --model=keras_earnings --json-instances=sample_input_prescaled.json



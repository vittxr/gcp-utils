# REF: https://cloud.google.com/compute/docs/machine-images/create-instance-from-machine-image?hl=pt-br#create-instance-from-different-project

# share image with another account
gcloud compute machine-images add-iam-policy-binding IMAGE_NAME \
 --project=PROJECT_ID \
 --member='serviceAccount:SERVICE_ACCOUNT_EMAIL_OF_DEST_PROJECT' \
 --role='roles/compute.admin'

# create image on desired project
gcloud compute instances create INSTANCE_NAME \
 --project=DEST_PROJECT_NAME \
 --zone=us-east1-b \
 --source-machine-image=projects/SOURCE_PROJECT_ID/global/machineImages/IMAGE_NAME \
 --service-account=SERVICE_ACCOUNT_OF_DEST_PROJECT

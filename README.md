# raccoondev.github.io

## GCP Bash Commands

External load balacner configuration:
```bash
gcloud compute regions list
gcloud compute zones list

export MY_REGION=<Enter YOUR_REGION here>
export MY_ZONE1=<Enter YOUR_ZONE1 here>
export MY_ZONE2=<Enter YOUR_ZONE2 here>

gcloud compute target-pools create extloadbalancer \
    --region $MY_REGION --http-health-check webserver-health
    
gcloud compute target-pools add-instances extloadbalancer \
    --instances webserver1,webserver2,webserver3 \
     --instances-zone=$MY_ZONE1
     
gcloud compute addresses list

export STATIC_EXTERNAL_IP=[YOUR_STATIC_IP]

gcloud compute forwarding-rules create webserver-rule \
    --region $MY_REGION --ports 80 \
    --address $STATIC_EXTERNAL_IP --target-pool extloadbalancer
     
```

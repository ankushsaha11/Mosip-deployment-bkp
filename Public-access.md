https://github.com/mosip/k8s-infra/blob/v1.2.0.2/docs/public-access.md

We need to make prereg, resident and esignet portal publicly accessible which is citizen centric




**Esignet and Resident portal is publicly accessible with below steps undertaken :**

1. We have added DNS records for esignet.mosip-sandbox.svgdev.net and mapped to public IP : 20.235.90.185 (No further changes for esignet)
   Similary, we have added DNS records for resident.mosip-sandbox.svgdev.net and mapped to public IP : 20.235.90.185.

2. In addition to adding DNS records for resident portal, we have also changed configmap configuration of resident-ui like below "baseUrl":"https://api-internal  ---> "baseUrl":"https://api.mosip-sandbox.svgdev.net

data:
    config.json: |-
      {"baseUrl":"https://api-internal.mosip-sandbox.svgdev.net/resident/v1",
       "version": "v1",
       "validateToken": "admin/authorize/admin/validateToken",



3. Going into resident-default.properties, changed to this --> - mosip.iam.module.redirecturi=${mosip.api.public.url}/resident/v1/login-redirect/

4. Then in the esignet database client_detail table we have changed the redirect url from api-internal to api.mosip

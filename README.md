# Simple Plausible Analytics for Kubernetes
A simple, self-hosted configuration for Plausible Analytics, meant for deploying to Kubernetes.

## Requirements:
- You have installed [Cert-manager](https://cert-manager.io/docs/) - optional (yet recommended). Responsible for auto-issuing ssl certificates for your host name. 
- You have an SMTP server which can be used by plausible to send emails

** Note:**
- By default, these templates will install everything in the `default` namespace (although, you're free to change that)
- Sections which need configuration have been marked as `<todo:replaceme>` for convenience

## The files:
- /base
  - /deployment.yaml       - the plausible deployment
  - /secret.yaml           - the plausible configuration and secrets 
  - /service.yaml          - simple plausible service definition 
  - /ingress.yaml          - the publicly accessible ingress config
  - /postgres.yaml         - simple postgres db instance from scratch
  - /clickhouse.yaml       - simple clickhouse db instance from scratch

## Getting started
1. Open `postgress.yaml`. Edit the `POSTGRES_PASSWORD` field and set a randomly generated password for the postgres database
2. Open `ingress.yaml`. Insert your chosen domain name into the host fields 
3. Open `secret.yaml`. Configure the marked fields.
4. Apply the configuration with `kubectl apply -f ./base`

## Read more:
- [The official plausible self-hosted docs](https://plausible.io/docs/self-hosting)
- [The official configuration options for plausible](https://plausible.io/docs/self-hosting-configuration)
# OADP-Velero

# Velero Backup and Restore Testing

This repository contains scripts and configurations to test the backup and restore of the `cakephp-mysql-persistent` application in an OpenShift cluster using Velero.

## Prerequisites

- OpenShift cluster with OADP Operator installed. FOllow below link for operator installation and for creating crd's
  -  https://docs.openshift.com/rosa/rosa_backing_up_and_restoring_applications/backing-up-applications.html
- Velero installed on your local machine.
  - Latest release of velero available here
    - https://github.com/vmware-tanzu/velero/releases/
- The application is installed in the `cakephp-mysql-persistent` namespace.
    - details in the file ./cakephp_test_application

## Setup

### 1. Backup the Application

First, create a backup of the application:

1. Verify that the `cakephp-mysql-persistent` namespace is backed up:
   ```bash
   oc create -f backup.yaml
   oc get backup -n openshift-adp cakephp-mysql-persistent-backup -o jsonpath='{.status.phase}'

### 2. Restore the Application
  ```
oc create -f restore.yaml
oc get restore -n openshift-adp restore-cakephp-mysql-persistent -o jsonpath='{.status.phase}'



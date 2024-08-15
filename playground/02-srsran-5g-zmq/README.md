## Playground 2 : srsRAN gNB and srsUE on K8S 
![TEEP-Progress(1)](https://hackmd.io/_uploads/r1jyItNF0.png)

This is my playground that I will install on the K8S Cluster. 

This setup uses 2 helm charts generated by Gradiant: open5gs and srsran-5g-zmq. These charts are packaged and available at Gradiant’s DockerHub repo: https://hub.docker.com/u/gradiant

### Setup Open5Gs Deployment

First, deploy the NGC (open5gs) using the ngc-values.yaml file provided in order to overwrite some of the default values of the Open5GS chart:

```
helm install open5gs oci://registry-1.docker.io/gradiant/open5gs --version 2.2.0 --values https://gradiant.github.io/5g-charts/docs/open5gs-srsran-5g-zmq/ngc-values.yaml 
```
These new values will:

* Disable the Open5gs EPC, deploying only the functions of the Open5GS 5G SA Core.
* Set the MCC, MNC and TAC to be used by the AMF.
* Enable the populate option, which will create a Deployment using the gradiant/open5gs-dbctl image. This will provide an easy way to manage the subscribers. In addition, the initCommands specified will register one subscriber initially, with the imsi, key, opc, apn, sst and sd provided.
* Disable the Ingress for accessing the Open5GS WebUI.

### Setup srsRAN-5G-ZMQ Deployment

Now, deploy the RAN (srsran-5g-zmq).

```
helm install srsran-5g-zmq oci://registry-1.docker.io/gradiant/srsran-5g-zmq --version 1.0.1
```
Thus, this deployment will not only launch the gNodeB, but it will also enable the launching of 1 UE using srsUE from the srsran-4g image.

It is important to notice that the default values of MCC, MNC, TAC, SST and SD set for the eNB match those configured in the open5gs chart. Also, the IMSI, KI and OPc given for the UE match the ones provided in the open5gs-dbctl command.

In addition, take into account that the value given for amf.hostname must match the name of the correponding AMF service deployed by the open5gs chart. Therefore, in case you use a differente release name for the open5gs chart, make sure that this value is set accordingly.


**Troubleshoot 1 - gNB Bind Address**
![image](https://hackmd.io/_uploads/HkHYRhEYR.png)
**Troubleshoot 2 - srsUE Pod**
![image](https://hackmd.io/_uploads/BknTAhVYC.png)
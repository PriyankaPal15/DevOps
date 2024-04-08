<Helm Fundamentals>:

Helm is a package manager for kubernetes. It looks at all the objects as part of a big package as a group.
During deployment of an application the user shall not ask it to look at which object but instead to act on which package to act on, like e.g., WordPress application package.
It helps us treat a kubernetes app as an app instead of bunch of objects. So one need not to micro manage each and every object in kubernetes cluster

<Advantages of Helm>:
1. One can install an application with a single command, like :- 
    # helm install <package-name>
2. Once can upgrade an application witha a single command, like :-
    # helm upgrade <package-name>
3. Same as for rollback, like :-
    # helm rollback <package-name>
4. Same as for uninstallation of an application, like :-\
    # helm uninstall <package-name>


<Install Helm>:
https://helm.sh/docs/intro/install

    <snap based system>:
        # sudo snap install helm --classic
    <apt based system>:
        # curl https://baltocdn.com/helm/signing.asc/ | sudo apt-key add -
        # sudo apt-get install apt-transport-https --yes
        # echo "deb https://baltocdn.com/heml/stable/debian/ all main " | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
        # sudo apt-get update
        # sudo apt-get install helm
    <package based system>:
        # pkg install helm

<HELM Concepts>:
values.yaml and template files together forms a HELM CHART.
A single helm chart may be used to deploy a single application like WordPress and it will have the all necessary template files for different services as well as the values.yaml files with the variables.
It also has a chart.yaml file that has information about the chart itself which includes, 
    a. name of the chart
    b. chart's version
    c. description of what the chart is
    d. keywords assiociated with the applications
    e. information about the maintainers

One can create their own chart for an application and also can explore the exisiting charts from the default repository i.e., 
    > https://artifacthub.io/
The artifact hub is the community driven repository but there are other available repositories too, such as 
    a. bitnami
    
<Helm Search Command>:   
# helm search hub <package-name>

To search for a chart in other repositories other than hub, one first must add the repository,
# helm repo add bitnami https://charts.bitnami.com/bitnami

Then, search for the chart with below command,
# helm search repo <package-name>

List existing repo,
# helm repo list

Once you find the chart the next step is to install the chart on your cluster,
# helm install [release-name] [chart-name]      ### with this command runs, the helm chart is downloaded from the repository and extracted and installed locally.

Each installation of a chart is called a release and each release has a release name. Each release is independent of each other. e.g.,
# helm install release-1 bitnami/<package-name>
# helm install release-2 bitnami/<package-name>
# helm install release-3 bitnami/<package-name>

Additional Helm Commands:
# helm list     ### to list down the installed packages
# helm uninstall <release-name>
# helm pull --untar bitnami/<package-name>       ### To only download and extracted a helm chart and not install it on the cluster
# ls <package-name>
# helm install <relesase-name> ./<package-name>


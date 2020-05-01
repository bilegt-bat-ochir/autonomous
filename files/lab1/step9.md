- [Go back to main](AutonomousWorkshop.md)
- [Go back to previous step](step8.md)

## Step 9: Manage Autonomous Database using OCI CLI

### Objectives ###
- Install OCI CLI 
- Be comfartable with OCI CLI
- Manage Oracle Cloud Infrastructure from command line

The CLI is a small footprint tool that you can use on its own or with the Console to complete Oracle Cloud Infrastructure tasks. The CLI provides the same core functionality as the Console, plus additional commands. Some of these, such as the ability to run scripts, extend the Console's functionality.

The CLI is built on Python (version 2.7.5 or 3.5 or later), running on Mac, Windows, or Linux. The Python code makes calls to Oracle Cloud Infrastructure APIs to provide the functionality implemented for the various services. These are REST APIs that use HTTPS requests and responses. 

We are going to see how to manage Autonomous database instances using OCI CLI.

- [Official Installation guide](https://docs.cloud.oracle.com/iaas/Content/API/SDKDocs/cliinstall.htm)
- [Getting started guide](https://docs.cloud.oracle.com/iaas/Content/API/SDKDocs/cliusing.htm#StartingCLI)

**Pre-requisites:**
1. An Oracle Cloud Infrastructure account
2. A user created in that account, in a group with a policy that grants the desired permissions
3. A SSH keypair used for signing API requests, with the public key uploaded to Oracle. Only the user calling the API should possess the private key.[Download your key](https://www.oci-workshop.com/keys/) from this link, it will automatically create a set of files for you.

4. Python version 2.7.5 or 3.5 or later, running on Mac, Windows, or Linux. Note that if you use the CLI Installer and do not have Python on your machine, the Installer offers to automatically install Python for you. If you already have Python installed on your machine, you can use the python --version command to find out which version is installed.

### Install OCI CLI ###

Use the command below to download and install the oci CLI and required software packages. During installation, you are prompted to specify where you would like to install the oci binaries. You are also given the option to update your $PATH environment setting and enable shell/tab completion.

To install OCI CLI on your local machine, 

Linux:

   ``` 
   bash -c "$(curl -L https://raw.githubusercontent.com/oracle/oci-cli/master/scripts/install/install.sh)"
   ```

Windows:

   ```
   powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/oracle/oci-cli/master/scripts/install/install.ps1'))"
   ```

- API key and SSH keys
In the OCI Web console, you must register the RSA public key that is associated with your oci CLI configuration. You must register the public key by using the API Keys section on the OCI console User Details page. [Generate your key](https://www.oci-workshop.com/keys/) using this link.  
   
- Upload your API public key in PEM format to OCI. Go to your Identity console, choose from the menu on the top left select **Identity->Users**. Once on the Users Page click on your username. Click **API Keys** under **Resources** on the left of the console, then click **Add Public Key**

![](/images/lab1/step9/0.API.PNG)

- After successfull upload, you will see the fingerprint of your ssh public key, copy that. It will be used for configuration in the later step

![](/images/lab1/step9/0.API-cont1.PNG)

- Configure OCI, use the command below to configure the OCI CLI. During configuration, you are prompted to specify the location where the configuration file is stored. 

```
C:\Users\BatOchir>oci setup config

Enter a location for your config [C:\Users\BatOchir\.oci\config]:
File: C:\Users\BatOchir\.oci\config already exists. Do you want to overwrite? [y/N]: y
Enter a user OCID: ocid1.user.oc1----------------------------------------------------------z7wa
Enter a tenancy OCID: ocid1.tenancy.oc1----------------------------------------------------------z7wa
Enter a region (e.g. ca-toronto-1, eu-frankfurt-1, uk-london-1, us-ashburn-1, us-gov-ashburn-1, us-gov-chicago-1, us-gov-phoenix-1, us-langley-1, us-luke-1, us-phoenix-1): eu-frankfurt-1
Do you want to generate a new RSA key pair? (If you decline you will be asked to supply the path to an existing key.) [Y/n]: y
Enter a directory for your keys to be created [C:\Users\BatOchir\.oci]:
Enter a name for your key [oci_api_key]:
Public key written to: C:\Users\BatOchir\.oci\oci_api_key_public.pem
Enter a passphrase for your private key (empty for no passphrase):
Private key written to: C:\Users\BatOchir\.oci\oci_api_key.pem
Fingerprint: d4:--:--:--:--:--:--:--:--:--:--:--:--:--:--:12
Config written to C:\Users\BatOchir\.oci\config
    If you haven't already uploaded your public key through the console,
    follow the instructions on the page linked below in the section 'How to
    upload the public key':
        https://docs.us-phoenix-1.oraclecloud.com/Content/API/Concepts/apisigningkey.htm#How2

```

You are also prompted to supply the user OCID, tenant OCID, and region that are associated with your Autonomous database instances. These values can be determined by examining the OCI Web console. 
Finally, you are prompted to specify an RSA key pair to use for request authentication. You need to choose same ssh key which you have uploaded to OCI console, and also need to use the same fingerprint.

### Use command line ###
Most commands must specify a service, followed by a resource type and then an action. The basic command line syntax is:
```
oci <service> <type> <action> <options>
```

For example, this syntax is applied as follows:

- compute is the <service>
- instance is the resource <type>
- launch is the <action>, and
- the rest of the command string consists of <options>.
The following command to list all accessible compartments in your tenancy.

```
oci iam compartment list --access-level ACCESSIBLE --all
```
The following command to list all database options available to you based on your access level.
```
oci db -h
```
### Manage Autonomous database using CLI ###

The following command to create an autonomous database in your compartment.
```
oci db autonomous-database create -c ocid1.compartment.oc1..aaaaaaaaqwv27hv7knzkbobfl6ucivtdmbkjn5h3cqxqeuzj2ac6ahkdioiq --db-name CLIdatabase --cpu-core-count 1 --data-storage-size-in-tbs 1 --admin-password PA##w0rd12345 --display-name myCLIdatabase --license-model LICENSE_INCLUDED
```

With following command you can stop/start yourautonomous database, you can even include this in bash script and schedule it. This is the great way to save your cost of running an Autonomous Database.

```
oci db autonomous-database stop --autonomous-database-id ocid1.autonomousdatabase.oc1.eu-frankfurt-1.abtheljtpp2dd4yya6uwwg4uhd7rmgcb6bxpked645lswh57xk2qyryad5ma

oci db autonomous-database start --autonomous-database-id ocid1.autonomousdatabase.oc1.eu-frankfurt-1.abtheljtpp2dd4yya6uwwg4uhd7rmgcb6bxpked645lswh57xk2qyryad5ma
```

### You may continue to next step ###
- [Load data into Autonomous Database](step10.md)

## Follow-up questions

![](/images/bilegt.jpg)

[bilegt.bat.ochir@oracle.com](mailto:bilegt.bat.ochir@oracle.com)

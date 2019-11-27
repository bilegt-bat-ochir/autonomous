## Step 9: Control your autonomous database using OCI CLI

**Pre-requisites: Create SSH Key Pair**
[Create an SSH Key Pair](#create-an-ssh-key-pair)

1. Open the OCI console. From OCI services menu, mouse-over **Compute** and click **Instances**

2. Click Create Instance. Fill out the dialog box:

   - **Name:** Enter a name
   - **Availability Domain:** Select the first available domain.(usually AD1)
   - **Image Operating System:** For the image, we recommend using the Latest Oracle Linux available.
   - **Choose Instance Type:** Select Virtual Machine
   - **Choose Instance Shape:** Select VM.Standard.E2.1
   - **Configure Boot Volume:** Leave the default
   - **Add SSH Keys:** Choose ‘Paste SSH Keys’ and paste the Public Key saved earlier.
   - **Virtual Cloud Network Compartment:** Choose your compartment
   - **Virtual Cloud Network:** Select the VCN you created in the previous section.
   - **Subnet Compartment:** Choose your compartment.
   - **Subnet:** Choose the first Subnet
   - Clik **Create**

**NOTE:** If 'Service limit' error is displayed choose a different shape such as VM.Standard.E2.2 OR VM.Standard2.2

![](/img/create-instance-01.png)
![](/img/create-instance-02.png)
![](/img/create-instance-03.png)

3. Wait for Instance to be in **Running** state. Connect via SSH tool of your choice.

4. Verify opc@<COMPUTE_INSTANCE_NAME> appears on the prompt

5. To install OCI CLI on the compute instance, Enter Command:


    `# bash -c "$(curl –L https://raw.githubusercontent.com/oracle/oci-cli/master/scripts/install/install.sh)"`

6.  When prompted for Install directory, Press Enter (choose default)

7. When prompted for ‘oci’ directory, Press Enter (choose default)

8.  When prompted for ‘Y/N’ for $Path, Enter Y, when prompted for path for rc file Press Enter (choose default)

9.  Check oci CLI installed version, Enter command:

    `# oci -v`

    ![](img/100_CLI_001.png)

    **NOTE:** Version should be minimum 2.5.X (3/23/2019)

10.  Next we will configure OCI CLI. Enter command:

     `# oci setup config`

11. Press Enter when prompted for directory name to accept the default. You will be prompted to enter user OCID


12. Switch to OCI Console window, Click user icon (Top Right of OCI Console Window) and click **User Settings**. In User settings click **copy** next to OCID for your user name

![](img/user-settings-01.png)
![](img/user-settings-02.png)

13. Switch to the SSH terminal session and paste the user OCID using mouse/touch pad and press Enter. You will be prompted to Enter Tenancy OCID

14. Switch to OCI Console window, Click user icon (Top Right of OCI Console Window) and click your Tenancy name, copy the OCID as was done for user OCID. Also note down your region (in this example "us-ashburn-1")

![](img/user-settings-01.png)
![](img/tenancy-ocid.png)

16. Switch to the SSH terminal window and paste the tenancy OCID using mouse/touch pad and press Enter. You will be prompted to Enter your region.

17. Type your region and press Enter. Enter Y for ‘New
RSA key pair’. Press Enter and accept default options for directories. Press Enter when prompted for passphrase (i.e leave it empty)

18. In the SSH terminal session for second compute, Enter command:

     ```
     # cd /home/opc/.oci
     # ls
     ```
    
Verify the API key files and OCI CLI config files exist.

19. Enter command

    `# cat config`

and ensure fingerprint exists. Leave the git-bash session open as we will verify the
finger print in config file aginst OCI, once we upload api
keys next.

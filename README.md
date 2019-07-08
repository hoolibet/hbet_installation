# HooliBet
Shell script to install a [HooliBet](https://HooliBet.com/) masternodes on a Linux server running Ubuntu 16.04. Use it on your own risk.
***

## Installation
```sh
wget -N https://raw.githubusercontent.com/hoolibet/hbet_installation/master/hbet_install.sh
bash hbet_install.sh
```
Wait until you request "Private Key" and paste your "masternode genkey" generated in the following steps.
***

## Desktop wallet setup  

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps:  
1. Open the HooliBet Desktop Wallet.
2. Go to RECEIVE and create a New Address: (Example): **MN1**
3. Send **1000** HBET to **MN1**. You need to send all amount coins in one single transaction.
4. Wait for 15 confirmations.  
5. Go to **Tools -> "Debug Window - Console"**  
6. Type the following command and copy the generated key to Notepad: **masternode genkey**  And **masternode outputs**
(Use **masternode genkey** in the VPS when you request "Private Key").
7. Go to  **Tools -> "Open Masternode Configuration File"**
8. Add the following entry:
    
    ```
    Alias Address Privkey TxHash TxIndex
    ```
    
    * Alias: **MN1**
    * Address: **VPS_IP:21340**
    * Privkey: **Masternode Private Key**
    * TxHash: **First value from masternode outputs**
    * TxIndex:  **Second value from masternode outputs**

    *Example:*
    
    ```
    mn1 127.0.0.1:21340 2S6Uekuw1G4SpRsMxLaZ3iKBoJkad3EucqeozTjov5bn6hNcsgx e6fd26786781131b1211ae579c4ef0f93a87878503bb22897cd388e0be16c5 0
    ```
    
9. Save and close the file.
10. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is run.
12. Select your MN and click **Start Alias** to start it.
13. Alternatively, open **Debug Console** and type:
    
    ```
    startmasternode alias 0 my_masternode_alias
    ```
    
    *Example: `startmasternode alias 0 MN1`*

14. Login to your VPS and check your masternode status by running the following command:

    ```sh
    hoolibet-cli masternode status
    ```

***

## Usage:
```sh
hoolibet-cli masternode status  
hoolibet-cli getinfo
```
Also, if you want to check/start/stop **HooliBet**, run one of the following commands as **root**:

```sh
systemctl status HooliBet #To check if HooliBet service is running  
systemctl start HooliBet #To start HooliBet service  
systemctl stop HooliBet #To stop HooliBet service  
systemctl is-enabled HooliBet #To check if HooliBet service is enabled on boot  
```

***

Credits:
https://github.com/zoldur

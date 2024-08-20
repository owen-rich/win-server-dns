# Windows Server: Configuring DNS

## Lab Mission
Configure DNS as a primary DNS server and add records.

## Resources
- **Environment & Tools**
  - VirtualBox
    - Windows Server 2016
    - Windows 10 Client

---

## Lab Task 1: Configure DNS
Add and resolve A and CNAME records.

1. On **SERVER1**, in **Server Manager**, click **Tools** and select **DNS**.
2. Expand **SERVER1 > Forward Lookup Zones > cyber.local**.
3. Right-click **cyber.local** and choose **New Host (A or AAAA)...**.
4. For **Name**, enter **test-client**; for **IP Address**, enter **10.0.0.10**; and click **Add Host**. Click **OK** when prompted.
5. Log into the Windows 10 client VM.
6. Open **CMD** and run the command `nslookup test-client.cyber.local`.
7. On **SERVER1**, in **Server Manager**, click **Tools** and select **DNS**.
8. Expand **SERVER1 > Forward Lookup Zones > cyber.local**.
9. Right-click **cyber.local** and choose **New Alias (CNAME)...**.
10. Under **Alias name**, enter **MY-FAVORITE-CLIENT**.
11. Click **Browse...** on the right, double-click **SERVER1**, double-click **Forward Lookup Zones**, then double-click **cyber.local**, and choose **test-client**. Enter `test-client.cyber.local` in the **Fully qualified domain name** field, then click **OK**.
12. Log into the Windows 10 client VM.
13. Open **CMD** and run the command `nslookup my-favorite-client.cyber.local`.

---

## Lab Task 2: Bonus
Configure a PTR record on SERVER1.

1. On **SERVER1**, navigate to the **DNS Servers** section, right-click **SERVER1** on the server panel, and select **DNS Manager**.
2. Right-click **Reverse Lookup Zones** and select **New Zone...**.
3. Click **Next** and select **Primary zone**.
4. In **Active Directory Zone Replication Scope**, select **To all DNS servers running on domain controllers in this domain: cyber.local** and click **Next**.
5. Under **Reverse Lookup Zone Name**, select **IPv4 Reverse Lookup Zone**, and click **Next**.
6. For the **Network ID**, enter **10.0.0**, leave the rest empty, and click **Next**.
7. On the **Dynamic Update** window, select **Allow both nonsecure and secure dynamic updates**, and click **Next**.
8. Click **Finish**.
9. Expand **Forward Lookup Zones** and select **cyber.local**. Double-click **test-client**.
10. Select **Update associated pointer (PTR) record** and click **OK**.
11. From the client machine, resolve the **10.0.0.10** IP using the `nslookup` command.

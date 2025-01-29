# Installation

%product% is a multiuser system containing a backend database that can run remotely
or as a local solution using either your network server or your local PC as a database server.

## Received an invitation?

%product% is about cooperation between company users and optionally external users.  
An administrator of an organization can invite internal users to join the organization.

External users like suppliers, customers or accountants can also be invited.

### When invited by your own organization

If you got invited by a system administrator <u>in your company</u> you can *skip the installation part*.
This is due to your administrator has already configured the system for you.

In that case you only need to install the app and accept the conditions from your admin.

After installation just choose **join my organization** and type the <tooltip term="OrganizationToken">organization token</tooltip>
you received in the invitation E-mail sent by your administrator.

After that you'll become a user of the organization you've joined.

### When invited by another company

If you received an invitation by another company the procedure is almost the same as above.

Install %product% from Microsoft Store, start the app and choose **accept invitation from [company]** where company is the remote
company that sent the invite to you.

## Determine installation type

If you're preparing an organization installation where multiple users should participate then you
should consider a hosted solution or a network server based installation for best results.

If you intend to use mobile clients or working from home a hosted database is best.

When all work is done inside your company and remote users connects through a VPN then a local
network server is the best installation type.

> %product% performs just as fast on a hosted database as on a local server.  
> This is due to all client PC's having their own replicated search index.
{style="note"}

## Hosted solution?

The easiest way to get started is using a hosted database and image repository.

<tooltip term="iEDI.com">iEDI.com</tooltip>, the developers of %product%, also offers ready-made database and image repository hosting 
which you enable directly from inside %product%.

On iEDI you'll get a 10GB free tier and for many companies this is a good start.

iEDI uses very fast hardware based on DDR5 RAM and Gen4 Nvme SSD storage.  
You free tier will include 1 CPU core, 2GB memory and 10GB storage space.

> Performance and Volume ?
>
> The free tier will handle ten's of thousands of daily documents and many users.  
> You basically only need upgrade if you run out of storage space.

Datacenters are placed in Scandinavia, Europe and USA.

The diagram below illustrates a hosted solution setup.

<code-block lang="mermaid">
sequenceDiagram
    box iEDI.app
    participant Backend
    end
    box Green Hosting Center
    participant Database
    participant Repository
    end
    box %product%
    participant Clients
    end
    autonumber
    Clients -->> Backend: API
    Backend ->> Database: Data
    Backend ->> Repository: Images
    Note over Database,Repository: Backup
    Repository -->> Clients: Sync
</code-block>

> GDPR Compliance  
> You can at any time remove all or some of your data and images
{style="note"}

> HIPAA Compliance  
> Data records are encrypted and can only be accessed using a PIN code
{style="note"}

## Local Installation

<procedure title="Configure installation">
    <p>To configure %product% for local server deployment.</p>
    <step>Install %product% on your PC through Microsoft Store</step>
    <step>Install %sync% on your PC through Microsoft Store</step>
    <p>Congratulations! You now have a %product%.</p>
</procedure>

> %product% will give the same user experience regardless of environment used

You've completed the installation.  
Next step will be creating your [First Product](../products/create-products).

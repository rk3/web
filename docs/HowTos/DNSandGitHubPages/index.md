---
layout: single
title: From DNS to GitHub Pages
toc: ture
---

## Intro
This describe the infrastructure configurations for this web site. from end to end. 
I get my DNS Name (ralfkremer.de) from [GoDaddy](https://www.godaddy.com/). GoDaddy also provide out of the box also a DNS Server. But this has limited configurations possibilities and functions. In my case I use a Azure DNS Server Service. Whit this I get the possibility to manage subdomains and a loot more. This Web Site is hosted at GitHub, generated with [Jekyll](https://jekyllrb.com/) (a static Web Site generator) and builded with a custom GitHub Workfow action. 

## DNS Name and Azure DNS Service Config

### Step 1 - Create Azure DNS Service
From the Azure Marketplace create a "DNS zone" Resource with all the necessary standard properties (Resource Group, Location ....)
![Azure Marketplace](/assets/images/HowTos/DNSandGitHubPages/AzureMarketplace.png)

When the "DNS zone" is created you will the in your DNS Resource Properties something similar to the next picture. The 4 different DNS Instances Name will be different for you. You will need the DNS Names for the next step.
![Azure Marketplace](/assets/images/HowTos/DNSandGitHubPages/AzureDNSServer.png)



### Step 2 - Forword DNS Name to Azure
I assume you created a DNS Name from GoDaddy. Navigate to your Domain Name and select "Manage DNS". ![Azure Marketplace](/assets/images/HowTos/DNSandGitHubPages/GoDaddyManage.png)
The next picture already show how the final configuration. The yellow marks Namer Severs are the from Azure. To get this you need to select "Change".![Azure Marketplace](/assets/images/HowTos/DNSandGitHubPages/GoDaddyNameConfig.png)
 This will open a Dialog with two main configuration Pathes. But you need to selekct the 3. option "Enter my own namesvers (advanced)"
![Azure Marketplace](/assets/images/HowTos/DNSandGitHubPages/GoDaddyNameConfigDialog1.png)
In the next dialog you need to enter your Azure Name Servers.
![Azure Marketplace](/assets/images/HowTos/DNSandGitHubPages/GoDaddyNameConfigDialog2.png)
I hope you can save all the chnages with out any error. 

### Step 3 - Create a Sub Domain
Go Back zu Azure and you DNS Server. There select "+ Recored set". In the following Dialog enter the subdomain name in the name field. As Type select CNAME. The Alias is you GitHub ID (in my case rk3) and "github.io." (the dot at the end is important).
![Azure Marketplace](/assets/images/HowTos/DNSandGitHubPages/AzureSubDomainCreate.png)
When new record should looks like the next picture.
![Azure Marketplace](/assets/images/HowTos/DNSandGitHubPages/AzureSubDomainDetails.png)

## GitHub Pages

### Step 1 - Create a git repo with GitHub Pages
descrption will come soon

### Step 2 - CNAME File
descrption will come soon

### Step 3 - Jekyll Configurations
descrption will come soon

### Step 4 - GitHub Repo Settings
descrption will come soon

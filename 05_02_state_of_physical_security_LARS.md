```{r, echo=FALSE}
source("programs/_plot_physical.R")
```

## Physically Protecting Sensitive Data

Within the Five Safes Framework, "safe settings" rely heavily on the physical environments in which data are stored, processed, transmitted, and accessed, and from which researchers can access computers that store and process the data. However, it is also the setting that is most dependent on rapidly evolving technology. In the 1980's, it was common and considered secure enough to send around floppy disks which researchers then inserted into stand-alone desktop computers in a locked room. Forty years later, network technologies allow for superior security combined with greater ease of access.

Possibly because technological advances happen faster than legal frameworks change, we have sometimes found that data custodians and policy makers may not be aware of the most current technological possibilities when crafting the legal and contractual framework for data access. This chapter will attempt to capture a snapshot of the technologies available and in use as of 2020. We will also attempt to characterize them along a multi-dimensional scale, allowing for some comparability across methods.  We then describe several examples, both from the case studies in this handbook as well as others that we are aware of.

We caution readers that by the time that this chapter is being read, the range of possibilities may yet again have expanded (rarely does it contract). Furthermore, the difficulty of implementing any given data access mechanism is contingent on the local conditions, skills, and available resources. Due to the many possible factors that go into a technological choice, we cannot make a comprehensive set of recommendations for data providers and researchers. What this chapter can provide are recommendations for a minimum baseline of security features that data access mechanisms should include and a framework for evaluating the tradeoffs between addressing likely threats while maintaining useful access and minimizing costs.

Readers must note that physical security is only one component of protecting individuals in data and safely using data for research, and cannot be considered on its own. The various technical measures described in this chapter are always implemented within the context of an overall access mechanism, and cannot be evaluated or ranked independently. Each case study in this handbook is an example of a global approach, of which technology is one component.

In this chapter, for illustrative purposes, we refer to a simplified structure in which data providers, researches, and possibly third parties are the parties involved in the process of storing and hosting data and computers. The introductory chapter and the [chapter on DUA] provide a more refined view of the various roles.

### Types of Security Threats

There are a variety of security threats, each with different levels of likelihood, severity, and considerations that are unique to the specific context of each data sharing agreement and access mechanism.^[@Chichonski_Computer_2012 provides definitions, which we will adopt here.] Depending on the context, actions taken to address any given threat may be (legally) required regardless of the burden on researchers and the cost of enforcing it. Data providers and researchers looking to set up new data access mechanisms should carefully judge the likely threats, their severity, and what cost-effective ways of addressing them are.

The archetypical threat to any computer system is the active, unauthorized access by adversarial actors ("hackers"). There are two main mechanisms in which this occurs. Adversarial actors can exploit technical vulnerabilities, such as improperly secured computer systems and networks, in the data access mechanism. They can also utilize [social engineering](https://csrc.nist.gov/glossary/term/social_engineering), which is the use of deception to manipulate individuals into revealing credentials to unauthorized users.^[It is called [phishing](https://csrc.nist.gov/glossary/term/phishing) when an email or website is used to deceive an individual.] There are many possible incentives for adversarial actors to compromise data: targeted attacks for the sake of exploiting specific data, targeting organizations to inflict financial or reputational harm, attacks of opportunity for financial or reputational gain, or functionally random targeting simply because they can. One cannot assume that any particular set of data is not of interest for adversarial actors merely due to the contents of the data or the organization that holds it.[REFERENCE]

> One example of a data breach due to adversarial actors exploiting technical vulnerabilities is the Equifax data breach of 2017.^[https://epic.org/privacy/data-breach/equifax/] Equifax neglected to apply security patches on their servers, leading to adversarial actors compromising their computer systems and the private information of over 148 million people.

A related security threat is the unintentional breach where data is left unsecured by authorized users. In this scenario, the data is breached not by any deliberate attempt by unauthorized users to gain access but by behavior on the part of authorized users that leaves it exposed, such as by losing devices that contain or can access data. These breaches can still lead to data ending up in the hands of adversarial actors seeking to exploit the confidential data. Like with adversarial actors, these measures are aimed at preventing unauthorized users from gaining access to the data when they should not, and different measures may be appropriate depending on the setting and sensitivity of the data. Collectively, deliberate attacks by adversarial actors and unintentional breaches can both be categorized as unauthorized access.

> There are numerous examples of data losses through the loss of laptops containing unencrypted data. Whether from employees of the government agency concerned -- the Veterans' Administration [@Bosworth_VA_2006] or the National Institutes of Health [@Greenemeier_Security_2008] -- or analysts at contractors or universities (for just one example, see @StanfordReport_Stanford_2008), most of these are probably inadvertent: the laptop stolen was the target for its resale value, not for the (probably unknown) value of the data it contained. Not all incidents are due to loss of electronic media - physical confidential records can also be lost through traffic accidents, for instance [@CBCNews_CRA_2019]. 

The third main category of security threats is where authorized users become bad actors and use the data in unauthorized ways. Unlike the other two threats, this is a situation where the threat comes from within the framework of the data access mechanism. This is an inherent risk in granting access to the data to outside users. Users may wish to conduct analyses that were unauthorized by the data provider, exploit the data for personal gain unrelated to its analytical use, or simply forget their obligations to protect the data. This kind of threat is in part addressed through non-technical means, in particular the choice of "safe people" and contractual and legal sanctions. However, restrictive data access mechanisms serve to address this threat as well.

> The Facebook-Cambridge Analytical scandal^[See @Confessore_Cambridge_2018 for an overview.] is an example of the misuse of data by otherwise authorized users. While the initial collection and analysis of Facebook user data by developers was within the bounds of Facebook's terms of service, a researcher subsequently provided the data to Cambridge Analytica in violation of those terms. This latter misuse was an unauthorized use by an otherwise authorized user. 

### Technical features of data access mechanisms

There are a variety of technical tools that can be used to protect against these security threats and are important for the implementation of secure data access mechanisms. In this section, we provide a non-exhaustive introduction to a list of important tools, systems, and concepts. These tools broadly correspond to protecting three components of data access mechanisms - the transfer and storage of data, the researcher's access to the data, and the secure locations for data access.  We then proceed to describe commonly used data access setups, the protections they provide, and their advantages and disadvantages. 


#### The Basics

All computer systems should follow the basic computer security mechanisms. While this may be standard practice for any centrally managed computers, at universities, corporations, and government agencies, many researchers may be self-managing their laptops. At a minimum, all computers should use a firewall and anti-virus software, have secure passwords, and apply basic computer hygiene, such as not using USB or other devices unless they are owned by the user (see for example guidance by [Microsoft](https://support.microsoft.com/en-us/help/4092060/windows-keep-your-computer-secure-at-home) and [Apple](https://support.apple.com/en-ca/guide/mac-help/flvlt003/mac).) When using storage servers, operating systems need to be kept up to date with security patches. Data providers and researchers looking to implement new or review existing data access mechanisms should consult with their institutions' IT and security staff.


### Storage of data

#### Physical media

Physical media is any device used to store data: hard-drives, solid-state drives, and removable media. 
Removable media include devices such as USB sticks, DVDs, and external hard-drives. These are typically used in the transfer of data between parties, such as from a data provider to a researcher. They are often disallowed on secure access or compute systems. On-site storage may be in the form of directly attached physical media, or network drives. 


#### Cloud Service

The use of cloud storage services^[As of 2020, AWS, Google Drive, Dropbox, Box, Microsoft OneDrive are all vendors of cloud storage services]. Cloud storage-like mechanisms can also be implemented by data providers or intermediaries, by using open source software such as [Nextcloud](https://nextcloud.com/).] is becoming more common, in particular in combination with cloud computing (see below). Utilizing cloud storage services may place the data under the control of a third party, which may be prohibited depending on the data sharing agreement or relevant legal constraints. 

#### Reliability as a criterion

Reliability of storage refers both to preventing data loss as well as maintaining system uptime. The risk of data loss can be mitigated by using one or more of the following techniques. Multiple disks can be organized in a redundant array (RAID) such that the failure of any one (or sometimes multiple) disks does not result in the loss of data. Robust automated backup strategies tailored to the risk tolerance as well as any legal or data use agreement requirements can be used. Backup strategies involving manual action -- plugging in a USB drive in combination with scheduled backup software -- are fallible, but may be considered as a last resort.

When using servers to store data, maximizing system uptime is important to allow for the uninterrupted use of data for research. Specialized storage servers allow for maintenance, including hot-swapping storage drives, while the server remains available for use. Similarly, having a USB drive with a current backup available mitigates the downtime should data be lost.

Online storage services implement these techniques as a normal part of their business, and may be one way researchers may leverage such techniques, if compliant with data use agreements. Furthermore, the ability to retrieve a backup copy or a previously versioned copy need not be implemented at every point. For instance, it may be sufficient for the data provider to implement backups for key data files. In case of data loss, the researcher can simply request a new copy of the file. However, researchers still will need to be able to backup their own code and derivative files. 

#### Encryption
Encryption is a cornerstone of information security. Fundamentally, encryption is process of encoding information using a process that prevents other parties from reading it without the encryption key. Data can be encrypted at rest - when not being used, stored on hard drives or USB sticks - and in transit - while being transferred over the network or on physical media such as DVD or USB sticks. 
Even though using encryption may decrease convenience (a password or a hardware key needs to be used each time decryption occurs), utilizing encryption for data and devices should be mandated as a minimum security feature part of any data access mechanism. In almost all cases, there is no added monetary expense for encrypting existing data and devices, in return for a substantial increase in protection against unauthorized access. IT staff, where available, should be well versed in these techniques. Individual researchers, if receiving data, should consult with IT staff on how to implement an appropriate strategy.  While utilizing encryption is a basic computer security best practice, it is of particular relevance for data access mechanisms due to the many methods of using encryption for storing and transferring data, with implementations described below.


Security in the context of data storage is the prevention of unauthorized access to the data should an adversary gain access to the storage device. On top of [data access controls] for users, the storage mechanism itself needs to be properly configured.  Keeping the data fully encrypted when not in use, known as encryption at rest, provides protection in the event that an adversary gets access to the storage device. Full disk encryption (FDE) of the storage device is when the entire hard drive is encrypted and needs to be unlocked before being used, and can be implemented with both hardware or software methods.^[In the case of hardware-based encryption, the disk needs to be decrypted before the operating system can boot, whereas operating system-based encryption relies on features of the operating system once it is booted. In practice, the differences from a user perspective are minimal.]

Full disk encryption occurs once when systems (servers, laptops) are booted up, and can be combined with [biometric authentication]. Data encryption may require that a hardware token be present any time data is processed, but such a hardware token may be embedded in the computer, or attached as a USB device.^[For instance, Windows bitlocker supports the use of both a trusted platform module built into modern computer motherboards as well as a startup key stored on removeable media (https://docs.microsoft.com/en-us/windows/security/information-protection/bitlocker/prepare-your-organization-for-bitlocker-planning-and-policies#bitlocker-key-protectors).] File-level encryption can also be used when using online storage systems. Operating system-level FDE is built into all major operating systems: [FileVault](https://support.apple.com/en-us/HT204837) on MacOS, [Bitlocker](https://docs.microsoft.com/en-us/windows/security/information-protection/bitlocker/bitlocker-overview) on modern Microsoft Windows operating systems, and various systems on Linux OS.^[https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019] If not using FDE, individual data files  (file-level encryption) or virtual encrypted disks can also be encrypted, and only decrypted when used. Popular software for file-level encryption, such as [GnuPG](https://gnupg.org/index.html), are free and easy to use, and available for all major operating systems. For virtual encrypted disks, [VeraCrypt](https://www.veracrypt.fr/en/Home.html) can be used.

In settings where cloud services are allowed, it is worthwhile to investigate the encryption practices of the cloud vendor. Many cloud vendors offer enterprise services that can meet higher standards of security suitable for meeting regulatory or legal requirements, or prevent the service provider from decrypting the data.  
However, while the cloud service may encrypt any data stored on its servers, the cloud storage service may be able (or even legally obligated) to be able to decrypt the data. A workaround is to use additional file-level encryption before making the file available on the cloud service, and this may in fact be mandated by the data sharing agreements.

### Transfer of data

Unless researchers access data at the data providers' computers and premises, data needs to be transferred. 

#### Transfer by physical media

Physical media intended for data transfers (USB keys, DVDs) should always be encrypted.  USB keys can be purchased with hardware-based encryption. When using physical media, the decryption keys (passwords) should always be transmitted separately; this prevents an unauthorized user who manages to obtain either the decryption key or the physical media from accessing the protected data. 
#### Secure Network Protocols

For data access mechanisms that rely on electronic transfers between the data custodian and researcher, using an encrypted transfer protocol is a minimum security practice that should be followed at all times. Some obsolete but commonly used transfer protocols do not use encryption, are therefore vulnerable to data being read in transfer, and should not be used. Any transfer protocols should be encrypted in transit. There are many network protocols used for transferring data or establishing secure connections between computers. Data may be transferred peer-to-peer, or may require the use of an intermediate party that sometimes is not signatory to the data use agreement. Secure peer-to-peer transfer can use the SSH File Transfer Protocol (SFTP), or authenticated transfer via HTTPS, the same protocol used by banks and most other modern websites, which encrypts the data sent between the client and server. Transfer over [virtual private networks] is also encrypted, regardless of transfer protocols, including for shared directory mounts (Windows shares, NFS). 
In settings where cloud services are allowed, data transfer is always encrypted. Encrypted cloud services can  fulfill the requirement for a minimally secure electronic transfer protocol. 

We note that while the transfer may be encrypted, both intermediate as well as final endpoints should also use encrypted [on-site storage]. As with cloud services, it may be useful to use file-level encryption to ensure that any intermediate storage locations do not compromise the security of the transfer mechanism. 


#### Data Access Controls

Data access controls are of particular relevance for systems where multiple researchers utilize the same computing resources for access to or analysis of data. Access control regulates what users can view or use in a computing environment, preventing unauthorized users from accessing confidential data. Access controls can be implemented by setting user permissions on directories at the operating system level on a computer. Another method is to use a virtual machine, which is a completely isolated computing environment running on a host computer. A host computer can run multiple virtual machines, with each researcher or research project having a specific virtual machine. Each virtual machine is configured to provide access only to a specific (limited) set of data files, as defined by the access permissions of the research team. In addition, software availability or network access can be customized on a per-project basis. Containers, popularly known as `Docker`, or Linux techniques such as `chroot`, achieve similar goals, with varying degrees of isolation and performance penalties.

#### Virtual Private Networks

When using Virtual private networks (VPN's), an encrypted channel is established between two computers over public networks. Once setup, the connection is as secure  as if these computers were connected on the same local, private network. The VPN ensures that a minimum security level is achieved by all other network connections, such as shared network drives or remote desktop access, as these all occur within the same encrypted channel.  This is useful for data access mechanisms that allow researchers to access data from a many possible locations as well as for data transfers As typically implemented, users must authenticate themselves with usernames, passwords, and often a secure token (2FA) to access the VPN. Many universities have VPN services that allow researchers to access university networks from a remote location. In instances where a data sharing partnership has to implement a VPN from scratch, such as setting up a VPN service at a data provider sharing data for the first time, there are VPN configuration settings built into the Windows Server operating system; open source options are also available.

#### IP Address Restrictions

When any network is involved, network access controls may be implemented. One way to ensure that only an authorized system has access to a remote system is to restrict the IP address of the devices that are allowed to connect to the server. This can be useful for performing data transfers as well as for remote access to data. There are two types of restrictions, blacklisting and whitelisting. Blacklisting specific addresses is used to block known or potential bad actors but otherwise does not restrict connections to the server; whitelisting only authorized users is the primary use of IP restrictions in an access control mechanism. This is frequently an option built into the software for managing the server. For example, software used for managing ||secure file transfer protocols|| can restrict the IP addresses that it will accept connections from. For data providers and researchers, this can be restricted to specific devices that the researcher registers with the data provider as the access computer. Other, more sophisticated network access controls may also be implemented, as dictated by any one of the involved parties' IT security staff. Restricting the IP address to specific devices can help protect against both unauthorized users, who would need to gain access to an authorized device, as well as allow for the monitoring of the whitelisted devices to guard against misuse of the data.

#### Remote Desktop

Remote desktop software (also referred to as Virtual Desktop Infrastructure, VDI) enables users to connect to another computer's desktop over a network. This can be used in data access mechanisms when the researcher does not have direct access to the data and performs their analysis remotely on a separate computer. Data custodians must configure the analysis computer to allow for incoming remote desktop connections, and the access provider must provide the appropriate software and network infrastructure to support the remote desktop connections from the access computer. Password and other authentication requirements help protect against access by unauthorized users. Analysis computers (typically servers) configured for remote desktop access typically run Microsoft® or Linux operating systems; clients to access the remote desktop exist on a variety of platforms, including cell phones and Apple computers. Vendors of such systems include [Microsoft®](https://www.microsoft.com/en-us/p/microsoft-remote-desktop/), [Citrix®](https://www.citrix.com/), [VMware®](https://www.vmware.com/), and [NoMachine®](https://www.nomachine.com/). Remote desktop connections are often channeled through a VPN for additional security.

The use of remote desktop software allows a researcher to use an analysis computer remotely, with the desktop environment of the analysis computer displayed on the client device, the access computer. The data custodian retains full physical control over the analysis computer. This can help prevent the misuse of data by authorized users. The use of remote desktop software can be valuable in instances where the data custodian has decided to not allow researchers to hold the data, in research data centers accessing data stored elsewhere, or when an access provider is supporting researchers across a wide geographical area, such as supporting international research on data that cannot leave its home country. The access computers also do not need to be capable of running statistical software or intensive analysis; the analysis will occur on the server that hosts the data and software packages. At the same time, the analysis computer, hosted by the data provider, must be capable of supporting multiple simultaneous researchers running analysis software. 

Remote desktops are reliant on active internet connections. While they are robust to network disconnects (users can simply reconnect to the running session and continue where they left off), the user experience degrades when network connections are unstable or slow.

#### Thin Clients

Thin clients are special case of an access computer running remote desktop client software. The primary benefit of thin clients is the extension of hardware control to the researcher's desktop by the data provider. Very secure implementations of thin clients can prohibit any usage beyond displaying information from the server and accepting mouse and keyboard input from the user. Thin clients typically operate without local storage, thus preventing users from saving data to the client. Thin clients can be secured with various login and authentication requirements that may be more stringent than the controls on researchers' own systems. Thin clients may be housed within a specific access location, or provided directly to the researcher. 

Generally, researchers would not procure their own thin clients, as they have no utility outside of facilitating remote access. Rather, they are typically provisioned by data custodians or access providers. The management and infrastructure needed to support thin clients may require expenses over and above the cost of providing remote desktop services. 

One of the main advantages of dedicated hardware thin clients is that they are cheaper and simpler than regular computers. As of the time of writing, thin clients can cost as little as $100 for the hardware itself, in contrast with the cheapest entry level computers which are several hundred dollars. Thin clients can be sourced from many manufacturers of enterprise hardware, both as standalone devices for the user to configure as well as full fledged hardware and software package solutions configured by the vendor (these will obviously cost more than just procuring the hardware). Thin clients can be purchased from most business PC vendors, including [Dell®](https://www.dell.com/en-us/work/shop/wyse-endpoints-and-software/sc/cloud-client/thin-clients), [HP®](https://www8.hp.com/us/en/cloud-computing/thin-clients.html), as well as some custom-produced solutions, such as the "[SD-Box](https://www.casd.eu/en/technologie/sd-box/)" developed by and produced for the Centre d'Accès Sécurisé aux Données (CASD).

#### Biometric Authentication

Biometrics are physical biological, and sometimes behavioral features unique to individuals. Biometric authentication](https://csrc.nist.gov/glossary/term/biometric) is the use of biometric features to verify the identity of individual users based on stored information about authorized users. One of the most common biometric technologies in current use is fingerprint scanners for consumer electronics such as laptops and smartphones. Other commonly used technologies include facial recognition, retinal or iris recognition, and voice identification. Biometrics can be used to control access to secured locations as well as to secure individual devices. The main components of such an access system includes the biometric sensor itself, which is connected to a database that contains the set of validated users, and either the physical or electronic lockouts for a given system (e.g. entering a room or logging into a computer) which are controlled by the biometric sensor.

Biometric authentication techniques can serve both as a primary form of identification as well as being layered in two or multiple factor authentication techniques, such as in conjunction with passwords or other devices.  While some devices come with built in biometric authentication, such as the aforementioned fingerprint scanners, implementing additional biometric authentication requires significant resources. In particular, the initial enrollment of users' biometrics typically requires the physical presence of the individuals.
 
#### Physical Access Cards

Physical access cards are electronic cards that identify the card bearer for a physical access control system. An access mechanism for devices or rooms secured by a card reader validates the user's card against a database that has a set of valid cards and subsequently opens the locks on the system or room that it is protecting. The cards themselves can use magnetic stripes, barcodes, chips, or other systems for interfacing with the card reader. Physical access cards are commonly used by many organizations, including universities and government agencies, and can have the advantage of using existing infrastructure to support the creation of secure access rooms for researchers receiving administrative data.  Unlike with biometric authentication, access cards can be easily lost or given to others, with a greater potential for misuse. Older systems may also be vulnerable to cloning attacks, where the magnetic stripe is copied to an unauthorized card. Protecting the access cards themselves is primarily a policy and training issue.

#### Secure Rooms

Rooms that house computing systems (both for storage and for access) can be secured against unauthorized access. Rooms can be constructed in ways that prevent unauthorized access, and can be outfitted to monitor usage and users.  Secure rooms may be required to be fully enclosed by walls that extend from floor to ceiling, have a small number of possible entryways, have doors, windows, air vents, and other possible entryways secured by bars, mesh, or other methods. Doors and walls may need to satisfy minimum specifications in terms of materials, construction techniques, and thickness to increase protection against physical attacks. For instance, reinforced doors and walls offer increased protection compared to regular home and office construction materials. Door hinges, access panels, partitions, windows, and other possible ways of entering the room may be installed from the inside of the secure room to prevent their removal from the outside. Additional requirements may extend to physically securing devices within the room. Computers may be required to have no outside network connections (a so-called "air-gapped network"), or no network connection at all. These restrictions are typically only utilized when mandated by data providers or required by law for the sharing of data. Building secure rooms is a costly endeavor, as few offices will meet these specifications without additional construction and hardening. Not all university campuses will have secure rooms, and when they do, there will often only be one secure room. Thus, access to secure rooms typically entails both long-distance and local travel, reducing overall accessibility. 

### Typical access mechanisms

The above technological methods can be combined in various ways, yielding an "access mechanism." The case studies in this handbook each implement one or more of these access mechanisms. In this section, we provide four archetypal examples of data access mechanisms. These are broad categorizations of how data access mechanisms can be set up, and are not an exhaustive list of possibilities.

#### Remote Execution

Under a ||remote execution|| model, a researcher submits a request to have the analysis executed on the confidential data by the data custodian.^[Remote execution systems are non-interactive - see [Virtual Data Enclave] for remote systems where access is interactive.] The researcher does not directly access the data, and can only view output shared back by the entity executing the analysis code. Data custodians maintain full control over the data, and have the opportunity to check the researchers' code prior to execution, and the output produced by the code prior to sharing back to the researcher. 

Remote execution requires that the data custodian maintains a mechanism for executing researchers' code, either through an automated service or having technical staff manually execute the analysis. The remote execution systems may also conduct disclosure avoidance checks on the output before sending it back to the researchers. These checks may also be conducted in automated fashions, or manually. In some cases, data providers prepare test files  - data files that have the same variables and table structures as the real data but contain fictitious values. 

The data custodian creates and maintains the systems to facilitate the transfer of the necessary files, through customized web portals or code upload facilities. While the input code and the output results by definition are non-sensitive files,  electronic [data transfer mechanisms][secure network protocols] may still be useful tools. In some instances, cost is recovered by charging researchers.

Remote execution gives the strong  protection against adversarial actors via the data access mechanism (breaches of a data provider occurring outside of the data access mechanism can still occur), though query attacks, in which attackers create overlapping queries or tabulations that reveal sensitive data, may still be possible [@asghar_averaging_2019]. Researchers have no opportunity to accidentally disclose research data. Data provider have strong protection against misuse of the data, as they have the opportunity to vet every analysis code prior to executing it or transferring the results back to the researcher. The tradeoff for the data provider is the cost of providing the necessary resources (systems and staff time) to conduct the analysis. 

Remote execution systems may have throttles and delays built in, to prevent resource abuse or query attacks. For instance, the number and runtime of analysis jobs for (registered) users may be severely limited, or carry an hourly cost. Researchers need to specify the analysis carefully, and iterative or exploratory analysis may be inhibited or reduced. For some researchers, this may be perceived as an impediment; however, for researchers working under a pre-registration paradigm, the same restriction may be neutral or even perceived as an advantage.

#### Physical Data Enclave

In a ||physical data enclave|| model, researchers must enter an access-controlled location (the "data enclave") to analyze the data. The data provider can act as its own data custodian or appoint a trusted third party to run the enclave on its behalf; enclaves under the control of the researcher are described under researcher provided infrastructure. The data custodian can choose to use [on-site storage] and computing at the data enclave or on a remote server that can only be accessed by [thin clients] located within the data enclave; in this case the connection to the remote server typically uses [secure network protocols],  [virtual private networks], or an encrypted direct connection. The data custodian typically has staff or automated systems to ensure that only authorized researchers enter the location, which may be secured with [biometric authentication] or [physical access cards]. Sometimes, the access rooms themselves satisfy specific security requirements ([secure rooms]). Output vetting may ensure that only safe outputs are removed from enclaves.

The data custodian has most of the security benefits of remote execution by maintaining full control over the data in the entire research process. Because the data remains under the control of the data custodian,  and secure rooms restrict physical access to approved users, it is secured against unauthorized access. Physical data enclaves remove the potential bottleneck and additional expense of requiring dedicated staff on the part of the data provider to actually run the analysis on behalf of the researcher.

However, physical data enclaves still impose restrictions on the flexibility of researchers. Instead of waiting for someone to run the remote execution for them, researchers have to schedule visits and travel to a physical location. Capacity limits may restrict the number of  users that can access the data at the same time.  In more basic implementations, a physical data enclave can be as simple as a locked room that only authorized users can enter. Meeting more stringent security requirements can impose a substantial initial start-up cost on new sites. This cost is often borne by the researchers' institution, and is too large for individual researchers to incur. 

#### Virtual Data Enclave

A ||virtual data enclave|| is conceptually similar to physical data enclaves. Data custodians still maintain servers that house the data. However, the requirement to access the data from a secure room is relaxed. Researchers have either many more choices for access, sometimes unrestricted, at other times being able to utilize their normal office or home to access the data via remote access.  There are two basic approaches to the remote access mechanism: either using [remote desktop] software that the researcher can install on their own computer, or  dedicated [thin clients] rented from or provided by the data custodian. As with physical enclaves, the data custodian typically also requires the use of [secure network protocols] or [virtual private networks] to access the data.

Virtual data enclaves retain most of the security benefits of physical data enclaves, except for physical control of the environment from which researchers access the data. In particular, as with physical data enclaves, data or output cannot be removed from the secure environment.  While virtual enclaves remain robust against unauthorized release of the data by keeping data stored in a secured environment and requiring authenticated access, it is possible for unauthorized individuals to view and potentially interact with the restricted access environment, for instance by "shoulder surfing" or if authorized users share credentials with unauthorized users. We note that legal and contractual requirements may still make such behavior explicitly illegal.

The virtual data enclave model do not require researchers to travel to specific facilities to perform their research, though some restrictions may still apply (IP addresses, university offices). While there may still be incentives to share costs for [thin clients], most virtual data enclaves are affordable for individual researchers.

#### Researcher-Provided Infrastructure

In some data sharing arrangements,  the researcher provides the [on-site storage] and analysis infrastructure. The data provider will transmit the data to the researcher through a secure transfer mechanism ([physical media], over [secure network protocols], or a [cloud service]). Providers typically require that data be encrypted at various stages of processing.

When the analysis environment is under the physical control of the researcher, the data provider has a significantly reduced ability to monitor  usage of the data. More so in this model than the others, the data provider depends on the contractual agreement with the researcher for preventing the misuse of the data, typically through a data use agreement specifying ||safe settings|| and the nature of ||safe outputs||.

This process allows researchers significantly more flexibility and rapid turnarounds on research findings. The overall cost is typically much lower, as the  data provider only has to provide the data  and the staff necessary to transfer it to the researchers. No separate staff or systems are needed to control exit or entry of people and monitor analysis outputs, since this is delegated to the researcher. Data providers may  choose to conduct  on-site inspections to verify adherence to contractual agreements of the ||safe setting||, verify at-rest encryption protocols, or attest to post-project destruction of data. Some providers require that researchers submit their output for approval, which requires staff time. 

### Five Aspects of Data Access Mechanisms

Actual implementations of data access mechanisms have many degrees of freedom in combining the technical components we outlined at the start of this chapter, and which the four typical setups combine in specific ways. Each of the case studies in this handbook is a variation of the basic types. In order to summarize the salient features of data access mechanisms, we categorize each data access mechanisms in five aspects:

- the level of **researcher agency over analysis computers** that they are allowed, referring to any technical restrictions on their usage of the analysis computers
- the physical **location of analysis computers and data**, which refers to the location of researcher-accessible computers used to analyze the data; for simplicity, we assume that the analysis computers are at the same location as the data
- the **location of access computers**, which are the computers (end points) that researchers use to access the data, which may be the same or separate from the analysis computers.
- the level of **access security**, referring to the overall  physical security arrangements for the environment and access computers from which  researchers can access the data.
- the **range of analysis methods available** to researchers, referring to any restrictions on the types of statistical analysis that researchers can perform on the data.

For each aspect, we classify a data access mechanism into three bins. These are weakly aligned with how restrictive it may be on the researcher, or conversely, how much control the data provider exerts, from high to low, but the mapping is not always exact. However, in all cases, there are distinct variants, which we will describe in the sections below. For convenience, we also define a simple visualization, mapping to colors, from high to low. (THIS NEEDS THE COLORS), allowing to compare multiple access mechanism visually.  The more restrictive category of each aspect is colored COLOR1, the least restrictive COLOR2.


Note we deliberately do not frame "control" as guaranteeing greater security. The level of security of any data access mechanism is dependent on a large number of factors, of which the technological features are merely one component. Proper implementation and maintenance of the technical infrastructure, compliance with restrictions outlined in the DUA, the training of users and staff, and other factors all contribute to the actual security of a data access mechanism.

When proposing and negotiating a potential use sharing agreement, evaluating the physical security arrangements along these five aspects can help researchers and their data providers craft robust mechanisms to protect data when transferring and using data for research.


Each of the five aspects of data access mechanisms have specific interactions with physical security. We further highlight such interactions in the descriptions of the five aspects and examples provided. In all cases, relaxing restrictions increases risk with respect to physical security ("safe environment"), but can be mitigated by measures in the other "safes," allowing data providers to maintain an acceptable risk-cost-usability tradeoff. The five aspects are not themselves fully independent either, but neither are they tightly aligned. Thus, it is possible to combine low restrictions on the location of analysis computers  with any level of agency over their configuration, or have highly restricted access environments combined with a wide range of restrictions on analysis methods.   

#### Researcher Authority over Analysis Computers

One of the key controls leveraged by data providers is the level of agency that researchers have over the analysis computer. Typically implemented through restrictions on operating system  configuration and software installation, the effect on researchers is the potential restrictions on the software that they can utilize. 
Data providers may choose to grant researchers only low or medium agency over analysis computers in order to increase computer and network security and as a mechanism for disclosure control. By restricting what users can do, such controls can help harden the analysis computers against direct threats from adversarial actors or researchers unwittingly installing malware on the analysis computers. 


In a **low agency setting**, researchers will be limited to the software that the data provider chooses to allow, and will not have administrative privileges over the analysis computer.^[These restrictions can affect not only the base software itself but also third party additions for those software such as third party packages for Stata, Python, and R.]

| Color1 | Color2 | Color3 |
|:---:|:---:|:---:|
| Low | Medium | High |


> The [Statistics Canada Real Time Remote Access (RTRA)] system is an example of a low researcher agency setting. Researchers can only use SAS and cannot directly view the data, with no exceptions allowed.

A **medium agency** setting may allow researchers some choice of software, or limited system configuration. For instance, they may be able to install, or request the installation, of supplemental packages for pre-approved software (R, Stata), but may not be able to change system parameters such as which network to use. Typically, data providers (or data intermediaries) have direct administrative control of such computers.


> An example of a system with medium researcher agency is the [FSRDC][Federal Statistical Research Data Centers (FSRDC)] network. The FSRDC has a specific set of software on their secure computing network that is made available to researchers. Additional software can be requested, which must be approved by program managers and security analysts.

In the **high researcher agency** settings, researchers have few restrictions on how the analysis computer can be configured. They may have administrative privileges to the analysis computer, and few if any  restrictions on the software that can be installed. The researcher may own and physically control the analysis computer, or may be granted administrative privileges to a computer that is owned by the data provider or third party. Data providers may still  mandate technical solutions such as the use of monitoring, operating system patch management software, or anti-virus software.

> One example with high researcher agency is the way that the [National Center for Education Statistics (NCES) restricted use data license] operates. The researcher must set up a secure data room in accordance with NCES requirements, but researchers provide and retain full administrative control over the analysis computer and can utilize whatever software they want.

The advantages of low agency are reduced likelihood of (inadvertent or intentional) unauthorized use of data. The cost of low or medium agency are varied. Restrictions on software may increase training costs for researchers. Restrictions on physical attributes of the analysis computers may increase the cost of providing more storage, or limit computationally-intensive analyses, slowing down research. Low agency shifts most of the burden of maintaining the analysis computer onto the data provider. Thus, the increased security of low agency is gained through slower research and higher costs for the data provider.


#### Location of Analysis Computers and Data

The location of the researcher-accessible data and the analysis computer defines who is considered  the data custodian in a data access mechanism. Note that this is distinct from agency over the analysis computer: the analysis computer may be physically located with researchers, but the researcher may have low agency over that computer (we provide an example later). We also abstract from situations where data storage and computing capabilities are in separate locations, as these situations are rare.^[All computing platforms as of the writing of this article require that data be transferred to the analysis computer's memory, thus necessarily co-locating data and analysis.]

Whoever houses the analysis computers and data still has maximum physical control and will need to provide the infrastructure and have the requisite technical staff to store the data and to set up the mechanisms for researchers to access the data. 

| Color1 | Color2 | Color3 |
|:---:|:---:|:---:|
| Data provider | Third party | Researcher |

The default situation is for the **data provider** to have custody of the analysis computer and data, acting as the data custodian. The data provider may choose to continue as data custodian when making data accessible  if there are specific legal or policy requirements for the data's location and security, and in taking into consideration the technical capabilities and trustworthiness of all parties involved.  Data providers that already have existing infrastructure that they can repurpose or already have  access mechanisms set up as part of their existing work may find this option to be particularly attractive. Furthermore, by acting as its own data custodian, transferring data is not a task that the data provider needs to consider.

> The German IAB Research Data Centers ("on-site access") house all highly confidential IAD data on own servers, which are accessed remotely by researchers from various locations. 

Data providers can choose a **third party** data custodian.  In general, third party data custodians (also called "data intermediaries") interact with multiple researchers, and may interact with multiple data providers. Third parties may have better or specific technical expertise, lower cost structures for the same level of security, and may leverage economies of scale in security and access mechanisms. Third parties can be government statistical agencies, acting on behalf of provincial or administrative government agencies, data centers at universities, or commercial entities. They may also have expertise in in combining data from multiple sources, while protecting the privacy of each source. For instance, government departments responsible for immigration and taxes may not be legally allowed to share data with each other, but they may each be able to transfer the data to a trusted third party. One particular area of expertise that we have observed that makes university-based third parties of interest to data providers is their familiarity with the requirements and use cases of researchers, enabling them to be more responsive to the needs of researchers. For instance, they may have particular expertise in survey management and data archiving, or in high-performance computing. Entities without their own research agendas may be particularly appealing as third parties, as that removes one of the incentives for the misuse of the data by an external data custodian. 

> The [Private Capital Research Institute (PCRI)] serves as a trusted third party for its data providers (private capital firms), and in turn contracts with a third party (National Opinion Research Center, NORC) to maintain analysis computers and a data access mechanism that has a third party data custodian. 

In some cases, the distinction between these two categories become blurred. A data provider with substantial expertise in making their own data accessible may offer this expertise to others, thus acting as third party data custodian.

> The United States [Federal Statistical Research Data Center (FSRDC)][Federal Statistical Research Data Centers (FSRDC)] network makes data from five US government agencies available. These include the Census Bureau, which created the FSRDC system in the 1980s as a network to provide access to Census Bureau data only. The FSRDC's  data and analysis computers continue to be located within the secure computing center of the  Census Bureau itself [@united_states_census_bureau_federal_nodate].

Finally, individual **researchers** can act as the data custodian. This is still quite frequently used, in particular when no previous data access existed. For the researcher, acting as the data custodian enables more flexibility for accessing the data without traveling or remote access systems. Most of the cost of maintaining IT infrastructure and security fall onto the researcher, subject to other conditions in the overall data access plan. Security provisions include keeping  analysis computer offline with no external network connections, or other provisions outlined earlier in this chapter. The enforcement of the DUA becomes a key mechanism for preventing the misuse of the data. 

> The [Aurora Healthcare and MIT] data exchange has the data and analysis computer located with the researcher. Researchers must store the data in accordance with security requirements outlined in their data use agreement.

Researcher agency over the analysis computer may also be limited, despite the researcher having full physical control of the analysis computer.
For instance, some data providers (often commercial companies) provide researchers with fully encrypted and remotely managed laptops. While the laptop is located with the researcher, the researcher has only low agency over the analysis computer.

In all cases where the data provider relinquishes the data custodial role,  data is transferred. While secure data transfer mechanisms exist, this is an additional risk within the overall framework, though as we described earlier, the cost is typically low to null. 

For data providers, transferring control of the data and analysis computers to a third party or directly to researchers might be desirable when support for many researchers is a burden for the regular business of the data provider. By transferring the data to another party, a data provider may no longer be responsible for the cost of providing computational infrastructure for [data storage][on-site storage] and analysis. However, the data provider may see some additional  costs for enforcing access restrictions, such as needing to conduct site visits, once physical custody of the data has been transferred. Data providers will rely on the enforcement of data use agreements when giving others custody of their data.

#### Location of Access Computers

In many cases, the analysis computer may not be physically accessible to the researcher. We therefore distinguish access computers, and restrictions that might be imposed on them as to their location and type. As a special case, the access computer can be co-incidental with the analysis computer.  Access computers can be located at the non-researcher data custodian, at a third party access provider, or with the researcher. The location of the access computer is not necessarily aligned with the ownership of the access computer. For instance, a researcher may be assigned a computer that serves as an access computer, but which is owned by the data provider. We discuss the security of the access computers in the next aspect, which is distinct from the locational aspect. 

| Color1 | Color2 | Color3 |
|:---:|:---:|:---:|
| Non-researcher data custodian | Third Party | Researcher |

If the access computer is located at the **non-researcher data custodian**, which can be the data provider or a third party custodian, the researcher must travel to their location. 

> The [New Brunswick Institute for Research, Data and Training (NB-IRDT)] is an example of locating access computers at the data custodian. Researchers wishing to use data held by NB-IRDT must travel to one of the NB-IRDT campuses to utilize the access computers. The access computers, in turn, connect over secure networks to the central analysis computers.


Data providers can choose a **third party** access provider. Note that the third party access provider need not be a data custodian. Researchers may still have to travel to a separate location. The key role played by third party access providers is control over physical access to the access computers (see next section). In some cases, third party access providers may also have the technical capability to maintain sophisticated network connections that are beyond the scope of individual researchers, such as [VPN] setups with dedicated encrypted endpoints. In other cases, it may simply be a way for multiple researchers to share the cost of using a mandated technical solution.^[The French CASD charges rent for its thin clients, and researchers sometimes locate such a thin client in a lab for shared access.] 

> The [SafePod Network (SPN)] in the United Kingdom is an example of locating access computers at a third-party access provider. Each individual SafePod, located at academic institutions, houses an access computer that provides remote access to the UK Administrative Data Research Network. [NEED LINK]

Finally, access computers can be located with the **researcher**. Trivially, locating the analysis computer with the researcher makes the access computer co-incidental. 

> An example of this is the [Ohio Longitudinal Data Archive (OLDA)], which requires that researchers use a computer that is registered with OLDA to download the data servers. This computer also serves as the analysis computer.

However, there are numerous cases where the access computer is with the researcher, when the analysis computer is not. Examples include any web-based access,  most [remote submission] systems, and many [remote desktop] systems: Researchers use their own computers to access the portal, while all computation occurs elsewhere.  In almost all cases, locating access computers with researchers  allows them to work from a location of their choice, though in some cases, this may be restricted to a designated university office. 

> An example of access computers located with the researcher is the [Institute for Employment Research (IAB RDC)] Job Submission Application (JoSuA) system. JoSuA is a web interface that researchers can use from their own computers to submit analysis files to the IAB RDC.

In general, the closer access computers are located to the data provider, the higher the security arrangements that apply. However, the two aspects are not perfectly correlated. In particular, access computers located with researchers can have very different security arrangements. 


#### Security of Access Computers

In addition to the location of access computers, the security of access to those computers can be vary substantially. This aspect encompasses both the location where the access computer resides, and the type of access computer.  We categorize security of access in three levels: high, medium, and low security. Data providers and researchers looking to set up new data access mechanisms should weigh the additional resource costs and barriers to research incurred by increasing access location security with the additional protections that higher security access locations provide.

| Color1 | Color2 | Color3 |
|:---:|:---:|:---:|
| High Security | Medium Security | Low Security |


In instances where a party other than the data provider maintains the access location, data providers typically have the right to approve the security arrangements, conduct audits, or otherwise directly verify that the operator is in compliance with the mandated security requirements. 

A **high security access location** has strong specifications for physical security, requiring the use of a [secure room][secure rooms], typically requiring additional hardening of the room beyond just access controls,  physical monitoring by video or access location staff, in addition to any electronic monitoring on the access computer itself. The additional protections and monitoring guard against unauthorized access as well as the removal of unauthorized outputs from the access location.

> The  [Federal Statistical Research Data Center (FSRDC)][Federal Statistical Research Data Centers (FSRDC)] network maintains a network of 29 locations[@united_states_census_bureau_federal_nodate]. While these secure rooms are located at partner organizations (universities, research centers, federal reserve banks), the rooms themselves are under the control of the U.S. Census Bureau, and none contain any data. Each secure room contains multiple [thin clients]. Researchers travel (across campus, or to a partner organization) to use the thin clients to access analysis computers  located within the secure computing center of the  Census Bureau  [@united_states_census_bureau_federal_nodate].

If not already existent at the access location, data custodians or access providers will require expertise from IT and security specialists to assist with defining the specifications and implementation of the features of high security access rooms.

A **medium security access location** has a defined location with access restricted to approved researchers. These can be rooms secured with [keycards][physical access cards], biometrics[biometric authentication], or a simple lock and key restricted to approved staff.  Such restrictions may be designed to prevent a limited set of unauthorized access attempts, or to inhibit "shoulder surfing" (visual inspection of output by unauthorized users). Medium security access rooms may incur additional costs for the location administrator, requiring dedicated space and staff to maintain the access location itself, but may also be as simple as a designated locked room at a university research institute.

> Data distributed under the [NCES restricted-use data license ][National Center for Education Statistics (NCES) Restricted Use Data License]  must be kept in a locked room with access restricted only to licensed researchers, with the security arrangements subject to random audits by NCES.

A **low security access location**  has few or no access controls. Simple restrictions might be broad geo-restrictions (campus-only) or procedures to follow. Data provider may mandate storing the access computer in a locked room, or can use [IP address restrictions]. When no access restrictions are imposed, researchers are free to use access computers from any location. 


In addition to the locational security described above, the **type of access computer** can also range from high security to low security. Highly-secure access computers -- which do not contain data -- may still include fully encrypted operating systems, the use of [VPN's][virtual private networks], [remote desktop] software, [secure network protocols], and [encryption] or requiring [biometric authentication] of the access computer. This can take the form of dedicated thin clients. Low-security access computers are typically allowed for remote submission or web portal-type access, where any computer, in any location, is allowed. 

> The [SFUSD-Stanford Partnership][San Francisco Unified School District (SFUSD)-Stanford Partnership] uses low security access locations. While the data is stored on secured servers at Stanford, researchers can access the data from anywhere as long as they take reasonable and appropriate efforts to keep the data secure from unauthorized access, as specified in their data use agreement.


We combine type of access and location into this aspect, since the ultimate convenience to researchers arises from a combination of the two security measures. For instance, a data provider might provide researchers with a dedicated secure laptop, which can only be used to remotely access the analysis computers - and nothing else. While there may be no location restrictions imposed on the researcher, the researcher is unlikely to carry two laptops around, and we would consider this to be a de-facto **medium** security solution.

The terms of the remote access will be defined in the DUA between the researcher and the data provider. The risks of locating the access computers, but not the analysis computers, away from the data provider are smaller. Because access computers contain no data, even if encrypted, the risk of inadvertent disclosure (for instance, if stolen) is reduced.  Remaining risks include "shoulder surfing" - when unauthorized users observe screens with confidential data while an authorized users is logged on. Using third parties to control access mitigates that risk. There is substantial convenience for researchers from having the access computer be closer to their usual place of work, increasing the speed of research. The growth of networks of research data centers, where access is shared amongst many users while data is mostly remote, is testament to the demand among researchers and the acceptability of the risk for many data providers. 


#### Range of Analysis Methods Available

The final aspect of data access mechanisms is the set of analysis methods available to researchers. Analysis methods can be unrestricted, subject to limited restrictions, or be subject to various restrictions. Methods  range from simple tabulations to complex machine learning algorithms via standard econometric techniques.

| Color1 | Color2 | Color3 |
|:---:|:---:|:---:|
| Highly Restricted | Limited Restrictions | Unrestricted |

These restrictions can be implemented for technical or security reasons, but mainly serve to ensure that researchers cannot misuse the data or generate unsafe output. Note that this aspect of data access mechanisms is distinct from the agency that researchers have over the analysis computer.  This aspect is closely related to the statistical protection of the data itself, affecting safe data and safe outputs. 

Restricting the analysis methods available to the researcher is primarily intended to protect the outputs of any analysis, preventing reidentification and other misuses of the data. Generally, the goal of restrictions on methods is to relax or automate output checks. Setting up such systems requires a high degree of technical sophistication and resources available to data custodians. Few off-the-shelf implementations of restricting analysis methods available. While this may be intended as a physical restriction on safe projects, researchers and data providers looking to set up new data access mechanisms should be clear on what restrictions may be placed on analysis methods and plan the research project accordingly.


When analysis methods are **unrestricted**, researchers can use the full set of methods available in the software that is available on the analysis computer, including any tabulation, or any regression analysis. Note that the ability to report on the results obtained via these methods might still be restricted, depending on what is considered "safe output."  Furthermore, the ability to access any method, for instance through add-on packages (e.g., SSC for Stata, or CRAN for R) may depend on the agency the researcher has over the analysis computer.

> [OLDA][Ohio Longitudinal Data Archive (OLDA)] is an example of unrestricted analysis methods, placing no limitations on the methods that researchers can use. OLDA relies on disclosure review, as mandated in their data use agreement, to ensure safe outputs.

When **limited restrictions** are imposed, some methods might be prevented, even if the software is available, by censoring elements of those softwares. In particular, the ability to inspect individual records may be limited. 

> An example of limited restrictions on analysis methods is the [IAB RDC][Institute for Employment Research (IAB RDC)] on site and JoSuA systems, where certain Stata commands are censored by the system and are unavailable to researchers, but broadly allows for most econometric techniques.

Analysis methods may be **highly restricted**. Restrictions can include limiting the methods available to researchers to a whitelisted set of commands or, in more extreme examples, limit them to the use of tabulator software that can only provide conditional tables. Most researcher will perceive this to impose strong limitations on their ability to conduct "research as usual,"  but such methods are sometimes used to reach a wide range of users, with relaxed conditions on the rest of the Five Safes framework.

> The [Statistics Canada Real Time Remote Access][Statistics Canada Real Time Remote Access (RTRA)] system only allows users to use a set of approved SAS commands. There are further limits on the number of variables and observations that can be included in analysis.


(removed "Revisiting" as redundant)

### Specific data access mechanisms along the five aspects

In this section, we evaluate several  data access mechanisms along the five aspects defined above. We have already alluded to some of these for individual aspects above, but here provide a comprehensive picture of all aspects. Some of these stem from the case studies in this handbook, others are  chapters. They are chosen to provide a spectrum of access mechanisms, focussing on variability in the five aspects, not representativeness. For each example, we provide a "badge" summarizing the five aspects visually. 


#### New Brunswick Institute for Research, Data and Training (NB-IRDT)

```{r, echo=FALSE, fig.width=5, fig.height=2}
plot_summary("NBIRDT",nbirdt,2,2,1,1,2)
```

The NB-IRDT (see [Chapter on NB-IRDT]) serves as a third party data custodian for the Province of New Brunswick to make deidentified personnel and health data available to researchers. The data and analysis computers are located at the central NB-IRDT facility, and researchers may travel there or to satellite NB-IRDT data centers to access the data via [thin clients] from [secure rooms], from which mobile devices and outside materials are banned. Thus, NB-IRDT serves as  non-researcher data custodian as well as a third party access provider to provincial data with high security. Researchers have medium agency over the analysis computers: access to common statistical programs is provided, and researchers can request other software packages.  The NB-IRDT allows researchers unrestricted analysis methods, relying on manual disclosure control to ensure safe outputs.

The NB-IRDT requires over two dozen staff^[https://www.unb.ca/nbirdt/about/team.html] located at the data custodian, including multiple data analysts, system administrators, and other technical staff to set up and maintain the data access mechanism. 

#### Institute for Employment Research (IAB RDC)

```{r, echo=FALSE, fig.width=5, fig.height=2}
plot_summary("IAB RDC",iab1,1,2,2,1,2)
```

The IAB RDC is an entity within the German Federal Employment Agency, separate from the administrative databases. It thus acts as an "internal third party" for the Employment Agency. The IAB RDC uses three different access models, each with its unique implementation. Notably, more sensitive data is subject to greater protections while maintaining usability for researchers.

The most restrictive access method is IAB RDC on-site access, which makes deidentified individual data available to researchers. The IAB RDC  maintains the data and analysis computers. Researchers have low agency over the analysis computers, being restricted to approved statistical software; other user provided software is not allowed, and third-party packages for approved software must be approved and installed by IAB RDC staff. Access computers ([thin clients] and secure workstations) can be located at the IAB RDC headquarters or at guest RDCs at various trusted institutions around the world, which then act as third-party access providers. The access locations are subject to high security, with physical monitoring of researchers and room access controls. 


```{r, echo=FALSE, fig.width=5, fig.height=2}
plot_summary("IAB JoSuA",iab2,2,2,3,3,2)
```

The JoSuA remote execution system allows researchers to utilize the same microdata, though they cannot view the data directly. Researchers are limited to viewing the deidentified output from their analysis, and there are some restrictions on Stata commands. In return, controls around access computers and locations are relaxed: Researchers utilize their own computers to use the JoSuA interface, and there are no restrictions on access locations. The data and analysis computer remains located with the IAB RDC, and researchers are subject to the same limitations on their agency over analysis computers and available analysis methods.

```{r, echo=FALSE, fig.width=5, fig.height=2}
plot_summary("IAB SUF",iab3,3,3,3,2,3)
```

The IAB RDC also makes data products ("scientific use files") available for direct download by researchers using a [secure download platform][secure network protocols], which are further anonymized variants of the microdata available in the other two access methods.  The researcher's institution acts as the data custodian by hosting the data and the analysis computer, with the researcher's institution having high agency over the analysis computer. The access computers and access location are also at the researcher's institution. The IAB RDC data use agreement for downloading the scientific use files requires a medium security access location, with the building and room required to have some level of access control or monitoring against unauthorized access; options range from receptionists and security guards to admission simple key locks. Note also that scientific use data can only be accessed by European research institutions.

The IAB RDC has a staff of over two dozen people^[https://www.iab.de/839/section.aspx/Bereichsnummer/17], not counting staff at guest RDCs. Each data center requires at least one staff member, as well as additional staff to maintain the data products and approve projects. 

#### Ohio Longitudinal Data Archive (OLDA)

```{r, echo=FALSE, fig.width=5, fig.height=2}
plot_summary("OLDA",olda,3,3,3,3,3)
```

The Ohio Longitudinal Data Archive is a third party data custodian that provides deidentified individual-level data to researchers on behalf of the state of Ohio. The data is initially located at OLDA before ultimately being transferred to researchers' analysis computers via an [SFTP server][secure network protocols]. The researchers have full agency over the analysis computer, which also serves as access computer. The computer must be physically located in the researcher's university office, and its [IP address][IP address restrictions]  registered with OLDA. There are no specific requirements imposed on the researcher's office (low security).  Researchers have unrestricted analysis methods available for them. 

OLDA relies on approximately a dozen full time staff to maintain its data access mechanism. It relies  on the statistical protections of the data ("safe data"),  the security of researchers' institutions, and on disclosure avoidance methods applied to outputs to keep data safe. 


#### Private Capital Research Institute (PCRI)

```{r, echo=FALSE, fig.width=5, fig.height=2}
plot_summary("PCRI",pcri,1,2,3,3,2)
```

The PCRI data access mechanism provides access to highly sensitive business information about private capital firms to researchers. Organizationally, PCRI serves as a third party data custodian, but in turn uses both the National Opinion Research Center (NORC) and in some cases the FSRDC system as a third-party location for the data and analysis computers. Researchers have low agency over the analysis computers, being restricted to the Stata on the NORC servers (see FSRDC for restrictions there). Researchers can only use [thin clients] that are provided to them by NORC. There are no formal restrictions on the location of the access computers, although researchers are required to use their best efforts to prevent unauthorized access. PCRI and NORC implement limited restrictions on the analysis methods available within Stata, prohibiting certain commands and sample sizes.

PCRI itself has three full time and six part-time staff to make the data usable for researchers, but relies on the preexisting resources at NORC for the data access mechanism. 

#### Federal Statistical Research Data Centers (FSRDC)

```{r, echo=FALSE, fig.width=5, fig.height=2}
plot_summary("FSRDC",fsrdc,2,1,1,1,3)
```

The United States Federal Statistical Research Data Center (FSRDC) network hosts data from multiple federal statistical agencies partner, serving as third party data curator and access provider. The data and analysis computers are hosted at the Census Bureau's computer center, separate from operational systems. Researchers have medium agency over these computers; they are restricted to authorized software but have the ability to request approval for additional software. Analysis methods are unrestricted. Access computers are [thin clients] located in [secure rooms] built by and located on the campuses of  partner institutions; however, the secure rooms remain under the control of and are considered part of the Census Bureau. Thus, while the system seems to have third party access providers, it is not [@united_states_census_bureau_federal_nodate]. Nevertheless, it serves as an interesting hybrid model.

Each of the currently 29 RDC locations has at least one full staff members, and the entire IT infrastructure is maintained by Census Bureau IT staff. Initial startup costs reach hundreds of thousands dollars. Partner institutions cover part of the cost of maintaining each RDC location [@united_states_census_bureau_hosting_nodate]. 


#### Statistics Canada Real Time Remote Access (RTRA)

```{r, echo=FALSE, fig.width=5, fig.height=2}
plot_summary("RTRA",rtra,1,1,3,3,1)
```

The RTRA system provides access to several Statistics Canada datasets. The data and analysis computers remain with Statistics Canada. Researchers have low agency over the analysis computers, and are  restricted to  using SAS. Access computers are not restricted - researchers can use any computer to submit jobs. Analysis methods are heavily restricted, with users limited to specific commands within SAS, restricted numbers of procedure calls a day, limits on class variables, and other controls on the SAS environment [@government_of_canada_system_2011]. 

The RTRA system is maintained by Statistics Canada, a major national statistical agency. Additional controls include automated controlled rounding of the outputs (safe outputs). and identification of safe users: registration and a contract are required for access, and researchers must be affiliated with a government department, non-profit organization, or an academic institution. We note that Statistics Canada also partners with the Canadian Research Data Center Network to provide access similar to the FSRDC system, with different data and unrestricted analysis methods.

#### SafePod Network (SPN)

```{r, echo=FALSE, fig.width=5, fig.height=2}
plot_summary("SafePod Network",safepod,2,1,2,2,3)
```

The SafePod Network in the United Kingdom makes de-identified administrative data from several UK administrative data providers available for researchers. A SafePod is a prefabricated room with a single [thin client][thin clients] with remote access. Analysis computers and data are located with the data provider, accessible through secure VPN connections [@university_of_bristol_safepod_nodate]. Each data provider decides about the agency level that researchers have over analysis computers and restrictions on analysis methods. For instance, at the Office of National Statistics, researchers have medium agency over the analysis computers and no restrictions on analysis methods [@office_for_national_statistics_accessing_nodate]. The unique aspect of the SafePod is the security of the access locations. SafePods are a minimalistic yet robust implementation of a medium security location (an access controlled space with CCTV monitoring) that can exist within low security environments such as university libraries.

SafePods are relatively cheap, requiring only a suitable location to place a prefabricated room and can use existing staff members to manage access to the SafePod. While the SafePod is still a physical location that requires installation and ongoing staff and maintenance, it is an example of innovation in more access locations to provide protection against the various security threats at a lower cost than a traditional full scale research data center.

#### National Center for Education Statistics (NCES) Restricted Use Data License

```{r, echo=FALSE, fig.width=5, fig.height=2}
plot_summary("NCES",nces,3,3,3,2,3)
```
The NCES, a part of the United States Department of Education, allows researchers to apply for a restricted use data license for de-identified individual level data on education. Under the terms of the license, the researchers serve as  data custodians and receive the data on an [encrypted CD][physical media] from NCES. Analysis and access computers are co-incidental, located with the researcher, subject to certain security configuration requirements for computer  and [storage of data][on-site storage]. Researchers have high agency over the analysis computer and are not restricted in the choice of analysis methods. NCES mandates a medium level of security for the access location, requiring that it must be a locked room with access restricted to authorized users but without additional specifications for security. The security arrangements must be approved by NCES prior to the receipt of restricted use data and are subject to unannounced inspections[@national_center_for_education_statistics_restricted-use_nodate].

The NCES restricted licenses require minimal resources for the data access mechanism; using physical media minimizes the technical resources needed to set up and harden a transfer mechanism. Researchers can utilize their existing university resources to set up the access location.  NCES relies on its disclosure review process (safe outputs) to protect against misuse.

#### Summary of examples

```{r extras, echo=FALSE}
plot_summary("OLDA",olda,3,3,3,3,3,display=FALSE)
plot_summary("Aurora",aurora,3,3,3,3,3,display=FALSE)
plot_summary("Cape Town",capetown,3,3,3,3,3,display=FALSE)
plot_summary("DIME",dime,3,3,3,3,3,display=FALSE)
```

```{r summary,echo=FALSE}
## This needs to be automated to replace the manually constructed figure below
## This might be ordered by some aggregate score (sum of the individual components)

   db.figures <- file.path(datadir,"figures0502.Rds")
   if ( file.exists(db.figures)) {
      db <- readRDS(db.figures)
#      knitr::kable(db)
   }
```

> We should create a more compact graph, and add to it the assessment for all the examples in the case studies (some of which were removed above)

<table>
<thead>
<tr class="header">
<th align="left">Name</th>
<th align="left">Summary</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">SFUSD</td>
<td align="left"><img height="100" src="figures/display_sfusd.png"></td>
</tr>
<tr class="even">
<td align="left">NBIRDT</td>
<td align="left"><img height="100" src="figures/display_nbirdt.png"></td>
</tr>
<tr class="odd">
<td align="left">IAB RDC</td>
<td align="left"><img height="100" src="figures/display_iab1.png"></td>
</tr>
<tr class="even">
<td align="left">IAB JoSuA</td>
<td align="left"><img height="100" src="figures/display_iab2.png"></td>
</tr>
<tr class="odd">
<td align="left">IAB PUF</td>
<td align="left"><img height="100" src="figures/display_iab3.png"></td>
</tr>
<tr class="even">
<td align="left">OLDA</td>
<td align="left"><img height="100" src="figures/display_olda.png"></td>
</tr>
<tr class="odd">
<td align="left">PCRI</td>
<td align="left"><img height="100" src="figures/display_pcri.png"></td>
</tr>
<tr class="even">
<td align="left">RTRA</td>
<td align="left"><img height="100" src="figures/display_rtra.png"></td>
</tr>
<tr class="odd">
<td align="left">FSRDC</td>
<td align="left"><img height="100" src="figures/display_fsrdc.png"></td>
</tr>
<tr class="even">
<td align="left">SafePod Network</td>
<td align="left"><img height="100" src="figures/display_safepod.png"></td>
</tr>
<tr class="odd">
<td align="left">NCES</td>
<td align="left"><img height="100" src="figures/display_nces.png"></td>
</tr>
</tbody>
</table>

### Guidance for Data Providers and Researchers

For data providers with the capacity and resources to implement sophisticated technological solutions, several  acceptable solutions that balance very high security with relatively broad accessibility and convenience exist. The IAB RDC on-site access model with international access, the NB-IRDT as a provincial system, and the national FSRDC network represent traditional, highly secured and  technically sophisticated methods of provisioning access today. The  UK SafePod Network is an attempt to reduce the technological cost of such a system. If some restrictions on analysis methods are acceptable,  the Statistics Canada RTRA and in particular the IAB RDC JoSuA remote access system  can be accessed from a wider range of locations and with fewer resources required.  

There are, however, also many examples of relatively simple but effective data access mechanisms, with typically lower costs. Mechanisms such as the NCES restricted use data license and OLDA leverage greater scrutiny on non-technological aspects with lower technological requirements, and let the researcher carry much of the burden of maintaining the access infrastructure. Protection of data at rest and in transit with the use of encryption and secure transfer mechanisms are relatively cheap to accomplish; the threat of adversarial actors can be  mitigated with a small investment in the proper physical resources.

> This next paragraph is not entirely accurate. Needs to be reformulated.

Another observation is that five aspects complement each other and they do not all need to be maintained under the tightest control to create the overall safe setting. While there is the temptation to always maintain the strongest possible protections across all aspects, existing mechanisms show that under the right conditions, a data provider can allow researchers more flexibility in some aspects while maintaining the overall security of the system. Perhaps the most direct example of this is the differences between the IAB RDC on site access versus remote access models. The same projects, people, and outputs are allowed in both models. Even the same sets of data can be used for analysis (NOT TRUE), with the only change between the two models being how much of that data is exposed to researchers via the data access mechanism. As a result of this change, the restrictions on access locations in the data access mechanism can be relaxed completely. This has the benefit of allowing much broader access to the data for researchers, with the associated increased utility of the data and additional potential for researchers generating findings relevant for policymakers.

The necessary aspects of a data access mechanism and the restrictions that are placed on the researchers' access to the data should be considered in the context of the other parts of the five safes framework. The conditions that a data access mechanism must provide to fulfill the requirements for safe settings are dependent on its interactions with the other four safes. DIME at the World Bank, OLDA, the SFUSD-Stanford Partnership, Aurora Healthcare and MIT, and the City of Cape Town and J-PAL partnership are all examples where the data providers from a spectrum of high, medium, and low income countries directly transfers highly sensitive individual level data and confidential government data that have great potential for harm in the event of disclosure. However, the proper protections of the data at the researcher and the fulfillment of the other aspects of the five safes data to the data provider's satisfaction allows the use of data access mechanisms that provide the researchers with a high level of flexibility.

A final related point is that the enforcement of the terms of the ||data use agreement|| is an important factor in determining the level of control that data providers must maintain over the data access system. In situations where the data provider grants greater autonomy to the researcher, the greater the complexity and strength of enforcement of the DUA provisions is required to compensate for that flexibility. This corresponds to a tradeoff between the investment in physical infrastructure and human resources necessary for tight control over a data access mechanism versus the investment in the institutional and legal framework of data access. In the partnerships above, the necessary protections in the data access mechanism are set in large part by the DUA.
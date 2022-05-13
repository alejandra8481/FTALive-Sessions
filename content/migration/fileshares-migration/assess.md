# Milestone: Assess and Select Target File Share Service
#### [prev](./overview.md) | [home](./readme.md)  | [next](./scan.md)

## Define and Gather File Services Requirements
The following table lists common file services requirements to be considered when planning to migrate file services to Azure. Knowing your requirements will help ensure you select the appropriate solution that meets your needs. 

| File Migration Requirements| Details |
| ------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Access methods for file data | What protocol(s) will clients use to access file data--SMB, NFS, HTTP/REST? Are there protocol version requirements, such as a newer version of a protocol to support a security feature? |
| Access patterns for files| Is file data access generally sequential or is there significant random read and write operations, such as with database files or virtual disk files? |
| Data tiering | Would tiering files across different storage types result in significant cost savings or performance benefits? For example, if 90% of files are old and rarely accessed, would it make sense for them to be on lower performance storage? |
| File type compatibility| What is the general description of your file data in each share? For example: user documents, application data and configuration, database files, etc.|
| Share structure and file hierarchy | How are your shares and the underlying file system organized? Do shares have specific performance requirements, classifications, environment levels, etc. or is file data in shares mixed?|
| Client connectivity method | Are clients permitted to access file data over the internet when the protocol implements encryption, or is it required that file data access traverse a VPN or ExpressRoute connection? |
| Data change locations| Will all changes to file data be made on a specific replica (such as on-prem) or at multiple locations (on-prem and in the cloud)?|
| Backup RPO, RTO, and retention requirements| How often will the file data need to be backed up? How quickly do you need to restore your data? How long will recovery points be retained and how many total recovery points will you require? |
| Data resiliency (locally-redundant in Azure region, zone redundant within a region, geo-replicated across regions) | Will your file data require redundancy beyond a single datacenter or region?|
| Share performance (IOPS) | How busy is each of your shares in your source environment, measured in IOPS? |
| End-to-end latency and client proximity| Do your clients have specific latency requirements when accessing file data? Will this require your file data to be located in close proximity to your clients? If so, how are clients located geographically?|
| Cost | Do you have specific requirements around the cost of your file solution in Azure which might limit your options?|
| Authentication and authorization | How will clients be authenticated and authorized when they access file data post-migration? Will filesystem-level permissions be required or are share-level permissions sufficient?|
| Cutover requirements for complete migrations (from the client perspective) | When it comes time to cut over to migrated files, will your clients have specific downtime requirements and schedules? How will clients be directed to new file services paths (if applicable)? |
| Migration timeline | How quickly does your migration need to be completed? |
| Anticipated future changes to file service requirements| Are there predicted to be changes to your file services requirements in the future which may impact your solution design? |

## **Choose a Target File Share Service** 
### Choose between IaaS vs. PaaS file shares.

Review this [table](https://docs.microsoft.com/en-us/azure/virtual-desktop/store-fslogix-profile#azure-platform-details) to help identify your initial file share cloud platform model. 
### Validate best fit scenario 

Review this [table](https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/ready/considerations/storage-options?toc=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Farchitecture%2Ftoc.json&bc=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Farchitecture%2Fbread%2Ftoc.json#file-and-object-storage-scenarios) to help identify your initial scenario and suggested PaaS file share service.
### Initial review for protocol, performance and limits

Review this [decision tree](https://docs.microsoft.com/en-us/azure/storage/common/storage-migration-overview?bc=/azure/cloud-adoption-framework/_bread/toc.json&toc=/azure/cloud-adoption-framework/toc.json#choose-a-target-storage-service) to help choose between Azure Files, Azure NetApps, and Blob Storage.

### Deeper Review to help choose between Blob, Azure Files and NetApps

Validate your selection via the below comparison tables to help make the final decision on a target file share service:
- [Table Comparison for Blob Storage, Azure Files and NetApps](https://docs.microsoft.com/en-us/azure/storage/common/nfs-comparison?toc=/azure/storage/files/toc.json)
- [Table Comparison for Azure and NetApps](https://docs.microsoft.com/en-us/azure/storage/files/storage-files-netapp-comparison)

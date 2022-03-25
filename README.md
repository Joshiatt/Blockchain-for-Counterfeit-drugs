# Blockchain-for-Detecting-Counterfeit-drugs using Hyperledger
Major negative implications of drug counterfeiting: 
  1. It results in a section of the society suffering from health issues. 

  2. Brand owners face a potential reputation risk. 

  3. There is a lack of transparency in drug distribution supply chains.


# How to Solve this ?

Serialisation as a Solution to Drug Counterfeiting

The serial numbers used can be easily replicated. To make replication difficult, Medicea built multiple levels of protection:
  1. The first level involved verification of authenticity as well as the entire trace. Such verification enables stringent control over distribution.

  2. The second level involved developing enhanced marking ink for printing the codes, which cannot be washed away. The ink is visible only under a certain type of monochromatic light.

  3. The final level involved the creation of an interoperable tracking system. The major features that this system needed to possess were as follows:

      1. It needed to be scalable across multiple clients, as Medicea’s solution is applicable to an entire market.

      2. It needed to be highly secure, as each client would want to independently maintain their channels, manage their operations and keep their data secure from tampering.

      3. It needed to be customisable and configurable so as to enable easy deployment across any sort of technical landscape and client business process.



For stock-keeping units (SKUs) that are cheaper, the first level of protection would be sufficient. For expensive SKUs, however, the second level of protection would also need to be deployed. To capture the movement of any SKU, the third level of protection, an interoperable tracking system is essential.



There are three major ways in which drug counterfeiting is executed: 

  1. The first method is when an entire factory is set up to manufacture counterfeit drugs under a different name. 

 2. The second method involves lapses of control in contract manufacturing, where drugs manufactured beyond requirement are routed through the black market. 

  3. The third method is by the reintroduction of expired drugs into the market. This is by far the method with the largest negative impact on all involved stakeholders.



How can serialisation enable companies to handle all three methods of counterfeiting? 

 1. It would be extremely difficult for factories manufacturing counterfeit drugs to find and replicate SKU-level serial numbers.

  2. Second, circulation of genuine drugs in the black market at the contractor’s end would not be possible, as serial numbers are not shared with them. So, the sale or movement of drugs will not be activated.

  3. And third, the reintroduction of expired drugs into the supply chain would not be possible, as the serial numbers help identify the reintroduced drugs and ascertain that they have expired and are counterfeit.




Serialisation can also be leveraged to provide two additional benefits: 

  1. The first is supply chain transparency. Using serial numbers to track products at the item level, companies would also reduce costs of their expired medicines, reduce instances of stock dumping and achieve pinpoint accuracy of item-level sales data. 

  2. The second is insurance fraud detection, where tighter controls can be enabled over high-priced products. So, recirculation or wrong usage can be prohibited, by considering purchases as uses and enforcing a single-use on each serial number. The result of such an application is observed in a reduction of health insurance costs, improvement of healthcare quality, transparent healthcare practices and complete utility of all purchases.


# Stakeholders


![fabric network 1](https://user-images.githubusercontent.com/22168000/160122786-fc1c1c66-4a9c-4b89-a754-ec83461d6b85.png)


# Workflow
The workflow required for the case study is divided into the following four units:

 
1. Company Registration: 
    1. All the entities who wish to be part of the supply chain network must be first registered or, in other terms, stored on the ledger. 
2. Drug Registration:
    1. As a part of this process, any drug manufactured has to be registered on the ledger by the manufacturing company. 
3. Transfer Drug:
    1. A buyer of the product will raise a Purchase Order for a particular drug.
    2. The Purchase Order will be generated for a batch of drugs. It will include information like the name of the drug, the quantity required, Buyer, etc.
    3. Based on the Purchase Order, the seller of the drug will initiate the process of shipment of the drug with the help of a transporter company like ‘FedEx’, and a shipment object will be created.
    4. The shipment object will contain information like, the name of the transporter, origin, destination, etc.
    5. Once the consignment is received by the buyer, the buyer will become the new owner of each item of the batch. 
    6. If the buyer is a consumer, then the Purchase Order and the shipment process need not be initiated. Only the owner of the drug is changed from the retailer to the consumer. 
4. View Lifecycle: 
    1. It is the process to view the lifecycle of the asset to date. 
    2. Imagine a consumer or a retailer wishes to view the lifecycle of a drug called ‘amoxicillin’ with serial number ‘medi-001’. The ‘View Lifecycle’ functionality of the smart contract will allow any participant in the network to view the entire lifecycle of the asset.



# Network Architecture

![fabric network](https://user-images.githubusercontent.com/22168000/160122880-d5e6c943-c89c-4798-8b45-ccf50cbf8f40.png)


# Smart Contract Architecture

![smart contract](https://user-images.githubusercontent.com/22168000/160123188-b1ad2117-1be7-451d-afa8-f2ba9cce939f.png)

I. Entity Registration
  1. registerCompany (companyCRN, companyName, Location, organisationRole)

          Use Case: This transaction/function will be used to register new entities on the ledger. For example, for “VG pharma” to become a distributor on the network, it must register itself on the ledger using this transaction.
 
II. Drug Registration
  1. addDrug (drugName, serialNo, mfgDate, expDate, companyCRN)

          Use Case: This transaction is used by any organisation registered as a ‘manufacturer’ to register a new drug on the ledger.

III. Transfer Drug
  1. createPO (buyerCRN, sellerCRN, drugName, quantity)

          Use Case: This function is used to create a Purchase Order (PO) to buy drugs, by companies belonging to ‘Distributor’ or ‘Retailer’ organisation.
 
  2. createShipment (buyerCRN, drugName, listOfAssets, transporterCRN )

          Use Case: After the buyer invokes the createPO transaction, the seller invokes this transaction to transport the consignment via a transporter corresponding to each PO.
     
  3. updateShipment( buyerCRN, drugName, transporterCRN)

          Use Case: This transaction is used to update the status of the shipment to ‘Delivered’ when the consignment gets delivered to the destination.   
      
  4. retailDrug (drugName, serialNo, retailerCRN, customerAadhar)

          Use Case: This transaction is called by the retailer while selling the drug to a consumer. 
      
      
IV. View Lifecycle
  1. viewHistory (drugName, serialNo)


      Description:
        This transaction will be used to view the lifecycle of the product by fetching transactions from the blockchain. 
        The function should return the transaction id along with the details of the asset for every transaction associated with it.
      
  2. viewDrugCurrentState (drugName, serialNo)
 

      Description:
        This transaction is used to view the current state of the Asset.
 




# GRINext
Proposed design and logical flow for GRINext business components.
#mermaid
sequenceDiagram
    par AccessionTrigger
    actor User
    User->>Accession: Delete
    activate Inventory
    Accession->>Inventory: Find(accession_id)
    Inventory->>DB: Select(inventory_id)
    alt exists
    Inventory-->>Accession: Inventory
    Accession->>Inventory: Delete(inventory_id)
    Inventory->>DB: Delete(inventory_id)
    end   
    deactivate Inventory
    end

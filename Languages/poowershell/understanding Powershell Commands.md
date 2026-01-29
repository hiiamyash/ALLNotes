
```powershell-session
Get-DomainObjectACL -ResolveGUIDs -Identity * | ? {$_.SecurityIdentifier -eq $sid} 
```

### **`-Identity *` Parameter**

- **`-Identity`**: Specifies which AD object(s) to examine
    
- **`*`**: Wildcard meaning **ALL** objects in the domain
    
- **Impact**: This queries EVERY object in Active Directory - can be slow/large in big domains
    
- **Alternative examples**:
    
    - `-Identity "Domain Admins"` (single object)
        
    - `-Identity "OU=Servers,DC=domain,DC=com"` (specific OU)
        

### **4. Pipeline `|`**

- **Symbol**: `|` (vertical bar)
    
- **Purpose**: Passes output from left command to right command
    
- **PowerShell concept**: The pipeline sends objects (not text) between commands
    

### **5. `?` (Where-Object alias)**

- **`?`**: Alias for `Where-Object` cmdlet
    
- **Purpose**: Filters objects based on a condition
    
- **Alternative**: Could write `Where-Object` or `| where`
    

### **6. `{$_.SecurityIdentifier -eq $sid}`**

- **`$_`**: Represents **current object** in pipeline
    
- **`.SecurityIdentifier`**: Property containing SID (Security Identifier)
    
- **`-eq`**: Equality comparison operator
    
- **`$sid`**: Variable containing a specific SID to match
    
- **Translation**: "Where the SecurityIdentifier property equals the value in $sid variable"


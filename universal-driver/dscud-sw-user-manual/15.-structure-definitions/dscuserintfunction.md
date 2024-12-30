# DSCUSERINTFUNCTION

Structure containing information about the user interrupt function and execution time.

### Structure Definition

```c
typedef struct { 

    DSCUserInterruptFunction func; 
    BYTE int_mode; 
    DWORD int_type; 
    
    } DSCUSERINTFUNCTION; 
    
    typedef void (*DSCUserInterruptFunction) (void* parameter); 
    
    // int_mode: user interrupt execution time choices 
    
    #define USER_INT_CANCEL 0 
    #define USER_INT_AFTER 1 
    #define USER_INT_INSTEAD 2 
    
    // int_type: which interrupt type to attach to 
    
    #define INT_TYPE_AD 0x01 
    #define INT_TYPE_DA 0x02 
    #define INT_TYPE_DIOIN 0x04 
    #define INT_TYPE_USER 0x08 
    #define INT_TYPE_COUNTER 0x10 
    #define INT_TYPE_DIOOUT 0x20 
    #define INT_TYPE_OPTO 0x40
```

### Structure Members

| Name      | Description                                                                                                                         | Applicable Boards                                                                              |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| func      | Pointer to user interrupt function of type DSCUserInterruptFunction                                                                 | Diamond-MM-16-AT,Diamond-MM-16RP-AT,Diamond-MM-32DX-AT,Diamond-MM-32X-AT,Diamond-MM-AT,Onyx-MM |
| int\_mode | Selects the execution time for the user interrupt function. Select from the choices in the list above. There is no "before" option. | Diamond-MM-16-AT,Diamond-MM-16RP-AT,Diamond-MM-32DX-AT,Diamond-MM-32X-AT,Diamond-MM-AT,Onyx-MM |
| int\_type | Selects the interrupt type to attach this function to (e.g. A/D interrupts, D/A interrupts, DIO interrupts, etc.)                   | Diamond-MM-16-AT,Diamond-MM-16RP-AT,Diamond-MM-32DX-AT,Diamond-MM-32X-AT,Diamond-MM-AT,Onyx-MM |

```pseudocode
Title: Specification of OpenVASP version 1.0
Author: Felix Laufenberg <felix.laufenberg@bitcoinsuisse.com>
Created: 2020-06-02
Document Version: 0.1
```
# Abstract

This document specfies the requirements that are mandatory as well as those requirements that are recommended for standalone OpenVASP clients (tequivalent to host + client in implementation architecture terminoligy). Recommended but not mandatory requirements will be marked as (recommended).  
The assumed baseline is the OpenVASP Whitepaper specification. This document specifies only the additions and changes made after the release of the Whitpaper.

# Requirements

## 1. (Addressing Layer) Index Contract Integration

### 1.1 VASP Code Type
A lookup table according, mapping VASP Code Type fields to VASP Index contracts must be implemented, representing the current mappings as specified in [ovip-0002](https://github.com/OpenVASP/ovips/blob/master/ovip-0002.md#211-vasp-code-type). 

### 1.2 Public Key Retrieval
Any compatible client software must be to look up another VASPs public encryption keys from a standardized VASP Index contract, given a VASP Identifier as specified in [ovip-0002](https://github.com/OpenVASP/ovips/blob/master/ovip-0002.md#216-vasp-identifier). 

## 2. Transport Layer Integration

### 2.1 ovip-0010
Any compatible client software must implement [ovip-0010](https://github.com/OpenVASP/ovips/blob/master/ovip-0010.md).

## 3. Authentication Layer Integration

### 3.1 VASP Whitelisting
Standalone software must have a simple UI which allows user to manage (add/remove/view) whitelisted VASPs. The software should send session replies automatically for whitelisted VASPs.

### 3.2 VASP Dictionary
The software must be able to securely retrieve VASP (legal entity) info from the VASP Dictionary (specification TBD)

## 4. Session Layer

### 4.1 ovip-0007
Any compatible client software must implement [ovip-0007](https://github.com/OpenVASP/ovips/blob/master/ovip-0007.md).

### 4.2 Persistance
Content and signature of Session Layer messages must be reliably persisted for 10+ years. The signature must be verifyiable against the stored content!

## 5. Application Layer 

### 5.1 Travel Rule Implementation
As defined in the original [Whitepaper](https://www.openvasp.org/wp-content/uploads/2019/11/OpenVasp_Whitepaper.pdf?cache=1).

### 5.2 Modular Implementation
(recommended) Flexibel solution architecture to easily add more application layer protocols later on.

## 6. Interfaces

### 6.1 User Interface 
Any standalone OpenVASP must allow a complete Travel Rule flow execution through the UI. All open Sessions must be visibel with all relevant information (exchanged data, current status, timestamps of last events).

### 6.2 Application Interface
Any standalone OpenVASP must allow a complete Travel Rule flow execution through the API.
The API endpoints must be well documented.

### 6.3 Host-Client Libraries
(recommended) It is recommended to publish a library which makes integration towards the OpenVASP Host easy. E.g. it wraps all API endpoints in functions.


# DeFi Liquidation Shield Protocol

A comprehensive DeFi protection system that automatically safeguards user positions from liquidation through intelligent collateral management, real-time risk assessment, and emergency intervention mechanisms.

## Overview

The DeFi Liquidation Shield Protocol provides multi-layered security for DeFi positions with automated position reinforcement, customizable risk parameters, community-backed emergency funding, and detailed liquidation analytics.

### Key Features

- **Continuous Position Monitoring**: Real-time health monitoring with intelligent risk alerts
- **Automated Emergency Response**: Automatic collateral deployment and position rescue
- **Customizable Protection**: User-defined protection thresholds and risk parameters
- **Community Emergency Fund**: Decentralized emergency response fund with governance
- **Comprehensive Analytics**: Detailed liquidation analytics and historical event tracking
- **Multi-signature Safety**: Emergency controls with protocol safety mechanisms

## Protocol Parameters

| Parameter | Value | Description |
|-----------|-------|-------------|
| Minimum Safe Collateral Ratio | 150% | Minimum safe collateralization level |
| Liquidation Danger Threshold | 120% | Risk threshold for liquidation alerts |
| Protection Service Fee | 1% | Fee for activating protection service |
| Maximum Emergency Amount | 1,000,000 STX | Maximum emergency intervention limit |

## Getting Started

### Prerequisites

- Stacks wallet with STX tokens
- Understanding of DeFi collateralization concepts
- Access to a Stacks blockchain node or API

### Installation

Deploy the smart contract to the Stacks blockchain:

```bash
clarinet deploy --network=testnet
```

## Core Functions

### Position Management

#### Add Collateral
```clarity
(add-collateral-to-position amount)
```
Adds STX collateral to your position to improve health ratio.

**Parameters:**
- `amount` (uint): Amount of STX to add as collateral

**Returns:** Updated total collateral balance

#### Remove Collateral
```clarity
(remove-collateral-from-position withdrawal-amount)
```
Removes collateral while maintaining safe collateralization levels.

**Parameters:**
- `withdrawal-amount` (uint): Amount of STX to withdraw

**Returns:** Remaining collateral balance

### Protection Services

#### Activate Protection
```clarity
(activate-liquidation-protection)
```
Enables automated liquidation protection for your position.

**Requirements:**
- Must have collateral in position
- Protection not already active
- Pays 1% service fee

#### Deactivate Protection
```clarity
(deactivate-liquidation-protection)
```
Disables liquidation protection service.

#### Configure Protection Parameters
```clarity
(configure-protection-parameters 
  enable-automatic-topup 
  emergency-contact-principal 
  maximum-intervention-amount 
  risk-threshold-level)
```

**Parameters:**
- `enable-automatic-topup` (bool): Enable automatic position reinforcement
- `emergency-contact-principal` (optional principal): Emergency contact address
- `maximum-intervention-amount` (uint): Maximum emergency rescue amount
- `risk-threshold-level` (uint): Custom risk alert threshold (120%-150%)

### Emergency Response

#### Execute Emergency Rescue
```clarity
(execute-emergency-position-rescue target-user-address rescue-collateral-amount)
```
Deploys emergency funds to rescue positions at risk of liquidation.

**Requirements:**
- Target user must have protection active
- Position must be below risk threshold
- Emergency fund must have sufficient balance

## Read-Only Functions

### Position Analytics

#### Get Position Details
```clarity
(get-user-position-details user-address)
```
Returns complete position information including collateral, debt, and protection status.

#### Calculate Health Ratio
```clarity
(calculate-position-health-ratio user-address)
```
Calculates the collateral-to-debt ratio for a position.

#### Check Liquidation Risk
```clarity
(check-position-liquidation-risk user-address)
```
Determines if a position is at risk of liquidation.

#### Get Protection Settings
```clarity
(get-user-protection-settings user-address)
```
Retrieves user's protection configuration.

### Protocol Statistics

#### Get Protocol Stats
```clarity
(get-protocol-statistics)
```
Returns comprehensive protocol metrics including total value protected and emergency fund balance.

#### Get Liquidation Event
```clarity
(get-liquidation-event-details event-identifier)
```
Retrieves details of a specific liquidation event.

## Security Features

### Risk Management
- **Minimum Safe Ratio**: 150% collateralization required
- **Liquidation Threshold**: 120% danger zone
- **Emergency Fund**: Community-backed rescue mechanism
- **Multi-signature Controls**: Administrative safety measures

### Access Control
- **User Functions**: Position management and protection configuration
- **Administrative Functions**: Protocol state management (deployer only)
- **Emergency Functions**: Automated rescue operations

## Usage Examples

### Basic Position Setup
```clarity
;; Add initial collateral
(add-collateral-to-position u1000000) ;; Add 1 STX

;; Activate protection
(activate-liquidation-protection)

;; Configure protection parameters
(configure-protection-parameters 
  true                    ;; Enable auto-topup
  (some 'SP123...)       ;; Emergency contact
  u500000                ;; Max intervention: 0.5 STX
  u1300)                 ;; Alert at 130% ratio
```

### Position Monitoring
```clarity
;; Check position health
(get-user-position-details tx-sender)

;; Calculate health ratio
(calculate-position-health-ratio tx-sender)

;; Check if at risk
(check-position-liquidation-risk tx-sender)
```

## Error Codes

| Code | Error | Description |
|------|-------|-------------|
| 1001 | ERR-UNAUTHORIZED-ACCESS | Insufficient permissions |
| 1002 | ERR-INSUFFICIENT-BALANCE | Insufficient funds |
| 1003 | ERR-POSITION-NOT-EXISTS | Position not found |
| 1004 | ERR-INVALID-AMOUNT-VALUE | Invalid amount parameter |
| 1005 | ERR-UNSAFE-COLLATERAL-RATIO | Would create unsafe position |
| 1006 | ERR-PROTECTION-ALREADY-ACTIVE | Protection already enabled |
| 1007 | ERR-PROTECTION-NOT-ENABLED | Protection not activated |
| 1008 | ERR-THRESHOLD-OUT-OF-BOUNDS | Invalid threshold value |
| 1009 | ERR-EMERGENCY-FUND-DEPLETED | Emergency fund insufficient |
| 1010 | ERR-PROTOCOL-CURRENTLY-PAUSED | Protocol temporarily disabled |

## Governance

### Administrative Functions
- **Protocol State**: Enable/disable protocol operations
- **Emergency Fund**: Manage community emergency reserves
- **Event Tracking**: Document liquidation events

### Community Features
- **Emergency Fund**: Community-contributed rescue funds
- **Protection Fees**: Sustainable fee model
- **Transparent Analytics**: Public liquidation event tracking
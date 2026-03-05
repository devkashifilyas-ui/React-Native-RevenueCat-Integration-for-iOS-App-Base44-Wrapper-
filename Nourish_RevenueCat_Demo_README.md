
# Nourish RevenueCat Integration Demo

This repository demonstrates a complete RevenueCat subscription integration workflow for a React Native mobile application.
The demo simulates how an iOS application handles subscriptions, free trials, entitlement validation, and restore purchases using RevenueCat and Apple In App Purchases.

The goal of this demo is to show the full architecture and purchase flow that would be implemented in a production application before an App Store launch.

---

## Project Overview

The demo represents the monetization system for an iOS application called Nourish: AI Food Scanner.
The app includes subscription based access where users must purchase a plan to unlock premium features.

Two subscription plans are configured.

Monthly Plan  
com.innerthoughts.nourish.monthly  
$4.99 per month

Annual Plan  
com.innerthoughts.nourish.annual  
$49.99 per year

Both plans include a 7 day free trial.

RevenueCat manages the subscription logic, entitlement validation, and purchase restoration.

---

## Demo Features

The interactive demo shows the full subscription lifecycle.

Home Screen  
Displays the user's subscription status and trial state.

Paywall Screen  
Shows both subscription options and triggers the purchase flow.

Premium Feature Screen  
Represents a feature that is locked until the user has an active subscription.

Developer Panel  
Shows entitlement status, subscription state, and trial information.

---

## What This Demo Simulates

The demo illustrates how a production mobile application handles:

RevenueCat SDK initialization  
Fetching subscription offerings  
Displaying paywall options  
Handling purchases  
Restoring purchases  
Checking subscription entitlement  
Locking and unlocking premium features

It also demonstrates how the application avoids common subscription issues such as false locks after purchase or incorrect entitlement states.

---

## Architecture Overview

React Native Mobile App

Subscription Store (Zustand or Redux)

RevenueCat SDK

Apple App Store In App Purchases

Entitlement Verification

Premium Feature Access

Every time the application launches it checks:

customerInfo.entitlements.active['premium_access']

This ensures users never lose access after a valid purchase or restore.

---

## Key Integration Files

revenuecatService.ts  
Handles SDK initialization and communication with RevenueCat.

subscriptionStore.ts  
Maintains subscription state and entitlement information.

PaywallScreen.tsx  
Displays available subscription packages and handles purchases.

---

## Purchase Flow

1. App initializes RevenueCat SDK.
2. App fetches available subscription offerings.
3. Paywall displays monthly and annual plans.
4. User selects a subscription plan.
5. RevenueCat processes the purchase.
6. CustomerInfo returns entitlement status.
7. App unlocks premium features if entitlement is active.

---

## Restore Purchases

If the user installs the app on another device, the restore button triggers:

RevenueCat restorePurchases()

RevenueCat returns the active entitlement and the application unlocks the premium features again.

---

## Trial Logic

Free trial configuration is handled inside App Store Connect.

RevenueCat automatically returns the trial status and remaining days through the CustomerInfo response.

No manual trial date calculations are required in the application.

---

## How to Use the Demo

Open the HTML demo file in your browser:

nourish-revenuecat-demo.html

Inside the demo you can:

Navigate between screens  
Simulate subscription states  
Trigger purchase flow simulation  
Test restore purchases logic  
View the architecture and integration flow

---

## Purpose of This Repository

This demo is designed to demonstrate how a RevenueCat integration would be structured before implementing it in a production application.

It helps clients and teams visualize:

Subscription architecture  
Paywall behavior  
Entitlement validation  
Purchase lifecycle

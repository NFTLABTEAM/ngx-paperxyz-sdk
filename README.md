# Paperxyz Angular Components

## Documentation

https://baxelson12.github.io/paper-angular-client-sdk/components/PaperCreateWalletComponent.html

## Usage

Import SDK module in app:

```javascript
import { PaperAngularClientSdkModule } from 'angular-client-sdk';

imports: [... PaperAngularClientSdkModule],
```

Implement in html:

```javascript
<div style="margin-bottom: 1rem; padding: 0.5rem 0">
  <label>Email:</label>
  <input type="text" [formControl]="control" />
</div>
<paper-create-wallet
  [emailAddress]="control.value!"
  [disabled]="!control.valid"
  chainName="Rinkeby"
  (success)="onCreateWalletSuccess($event.walletAddress, $event.emailAddress)"
  (error)="onCreateWalletError($event.code, $event.error)"
  (emailVerificationPending)="onCreateWalletVerificationPending()"
>
  Verify email
</paper-create-wallet>

<br />
<br />

<paper-pay-with-card
  *ngIf="email"
  chainName="Rinkeby"
  checkoutId="7b2264ab-2533-4bf6-9569-7a5b3af52332"
  [recipientWalletAddress]="wallet"
  [emailAddress]="email"
  [quantity]="1"
  (paymentSuccess)="onCheckoutPaymentSuccess($event.id)"
  (transferSuccess)="onCheckoutTransferSuccess($event.id)"
  (review)="onCheckoutReview($event.id)"
  (cancel)="onCheckoutCancel()"
  (error)="onCheckoutError($event.code, $event.error)"
></paper-pay-with-card>
```

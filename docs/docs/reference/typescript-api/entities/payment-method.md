---
title: "PaymentMethod"
weight: 10
date: 2023-07-20T13:56:15.263Z
showtoc: true
generated: true
---
<!-- This file was generated from the Vendure source. Do not modify. Instead, re-run the "docs:build" script -->
import MemberInfo from '@site/src/components/MemberInfo';
import GenerationInfo from '@site/src/components/GenerationInfo';
import MemberDescription from '@site/src/components/MemberDescription';


## PaymentMethod

<GenerationInfo sourceFile="packages/core/src/entity/payment-method/payment-method.entity.ts" sourceLine="21" packageName="@vendure/core" />

A PaymentMethod is created automatically according to the configured <a href='/typescript-api/payment/payment-method-handler#paymentmethodhandler'>PaymentMethodHandler</a>s defined
in the <a href='/typescript-api/payment/payment-options#paymentoptions'>PaymentOptions</a> config.

```ts title="Signature"
class PaymentMethod extends VendureEntity implements Translatable, ChannelAware, HasCustomFields {
  constructor(input?: DeepPartial<PaymentMethod>)
  name: LocaleString;
  @Column({ default: '' }) @Column({ default: '' }) code: string;
  description: LocaleString;
  @OneToMany(type => PaymentMethodTranslation, translation => translation.base, { eager: true }) @OneToMany(type => PaymentMethodTranslation, translation => translation.base, { eager: true })
    translations: Array<Translation<PaymentMethod>>;
  @Column() @Column() enabled: boolean;
  @Column('simple-json', { nullable: true }) @Column('simple-json', { nullable: true }) checker: ConfigurableOperation | null;
  @Column('simple-json') @Column('simple-json') handler: ConfigurableOperation;
  @ManyToMany(type => Channel) @JoinTable() @ManyToMany(type => Channel)
    @JoinTable()
    channels: Channel[];
  @Column(type => CustomPaymentMethodFields) @Column(type => CustomPaymentMethodFields)
    customFields: CustomPaymentMethodFields;
}
```
Extends

 * <a href='/typescript-api/entities/vendure-entity#vendureentity'>VendureEntity</a>


Implements

 * <a href='/typescript-api/entities/interfaces#translatable'>Translatable</a>
 * <a href='/typescript-api/entities/interfaces#channelaware'>ChannelAware</a>
 * HasCustomFields



### constructor

<MemberInfo kind="method" type="(input?: DeepPartial&#60;<a href='/typescript-api/entities/payment-method#paymentmethod'>PaymentMethod</a>&#62;) => PaymentMethod"   />


### name

<MemberInfo kind="property" type="LocaleString"   />


### code

<MemberInfo kind="property" type="string"   />


### description

<MemberInfo kind="property" type="LocaleString"   />


### translations

<MemberInfo kind="property" type="Array&#60;Translation&#60;<a href='/typescript-api/entities/payment-method#paymentmethod'>PaymentMethod</a>&#62;&#62;"   />


### enabled

<MemberInfo kind="property" type="boolean"   />


### checker

<MemberInfo kind="property" type="ConfigurableOperation | null"   />


### handler

<MemberInfo kind="property" type="ConfigurableOperation"   />


### channels

<MemberInfo kind="property" type="<a href='/typescript-api/entities/channel#channel'>Channel</a>[]"   />


### customFields

<MemberInfo kind="property" type="CustomPaymentMethodFields"   />


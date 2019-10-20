---
title: 'Arquivo XSD de exemplo: esquema simples'
ms.date: 11/04/2016
ms.topic: sample
ms.assetid: f7e1dde1-b4f6-4371-add4-935b68ec77d7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b6681e47ba33d16cd48f5f34389a5d113fc36ef
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651169"
---
# <a name="sample-xsd-file-simple-schema"></a>Arquivo XSD de exemplo: esquema simples

O arquivo XSD a seguir é usado em vários exemplos na documentação do Designer de Esquema XSD. Esse arquivo é um esquema de ordem de compra simples.

```xml
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
           xmlns:tns="http://tempuri.org/PurchaseOrderSchema.xsd"
           targetNamespace="http://tempuri.org/PurchaseOrderSchema.xsd"
           elementFormDefault="qualified">
 <xsd:element name="PurchaseOrder" type="tns:PurchaseOrderType"/>
 <xsd:complexType name="PurchaseOrderType">
  <xsd:sequence>
   <xsd:element name="ShipTo" type="tns:USAddress" maxOccurs="2"/>
   <xsd:element name="BillTo" type="tns:USAddress"/>
  </xsd:sequence>
  <xsd:attribute name="OrderDate" type="xsd:date"/>
 </xsd:complexType>

 <xsd:complexType name="USAddress">
  <xsd:sequence>
   <xsd:element name="name"   type="xsd:string"/>
   <xsd:element name="street" type="xsd:string"/>
   <xsd:element name="city"   type="xsd:string"/>
   <xsd:element name="state"  type="xsd:string"/>
   <xsd:element name="zip"    type="xsd:integer"/>
  </xsd:sequence>
  <xsd:attribute name="country" type="xsd:NMTOKEN" fixed="US"/>
 </xsd:complexType>
</xsd:schema>
```

> [!NOTE]
> As empresas, as organizações, os produtos, os nomes de domínio, os endereços de email, os logotipos, as pessoas, os locais e os eventos de exemplo descritos aqui são fictícios. Nenhuma associação com nenhuma empresa, organização, produto, nome de domínio, endereço de email, logotipo, pessoa, locais ou eventos reais é intencional nem deve ser inferida.
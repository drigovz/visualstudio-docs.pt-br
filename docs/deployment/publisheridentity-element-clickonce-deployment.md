---
title: '&lt;&gt;elemento publisherIdentity (implantação do ClickOnce) | Microsoft Docs'
description: O elemento publisherIdentity contém informações sobre o Publicador que assinou um manifesto de implantação. O elemento é necessário para manifestos assinados.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 65f225f8e3dd3f6d2b3afb2d2a5284d172d4fab1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891287"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;&gt;elemento publisherIdentity (implantação do ClickOnce)
Contém informações sobre o Publicador que assinou este manifesto de implantação.

## <a name="syntax"></a>Sintaxe

```xml
<publisherIdentity
   name
   issuerKeyHash
/>
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 O `publisherIdentity` elemento é necessário para manifestos assinados. A tabela a seguir mostra os atributos aos quais o `publisherIdentity` elemento dá suporte.

|Atributo|Descrição|
|---------------|-----------------|
|`name`|Obrigatórios. Descreve a identidade da entidade que publicou este aplicativo.|
|`issuerKeyHash`|Obrigatório. Contém o hash SHA-1 da chave pública do emissor do certificado.|

#### <a name="parameters"></a>Parâmetros

## <a name="property-valuereturn-value"></a>Valor da propriedade/valor retornado

## <a name="exceptions"></a>Exceções

## <a name="remarks"></a>Comentários

## <a name="requirements"></a>Requisitos

## <a name="subhead"></a>Subtítulo
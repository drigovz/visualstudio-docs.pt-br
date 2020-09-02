---
title: '&lt;&gt;elemento publisherIdentity (implantação do ClickOnce) | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 995b002784c1e76ceed36e51edb1ae893448f448
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62927533"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;&gt;elemento publisherIdentity (implantação do ClickOnce)
Contém informações sobre o Publicador que assinou este manifesto de implantação.

## <a name="syntax"></a>Syntax

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
|`issuerKeyHash`|Obrigatórios. Contém o hash SHA-1 da chave pública do emissor do certificado.|

#### <a name="parameters"></a>Parâmetros

## <a name="property-valuereturn-value"></a>Valor da propriedade/valor retornado

## <a name="exceptions"></a>Exceções

## <a name="remarks"></a>Comentários

## <a name="requirements"></a>Requisitos

## <a name="subhead"></a>Subtítulo
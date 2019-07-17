---
title: '&lt;publisherIdentity&gt; elemento (implantação do ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 486e0bc5059e041f02e8dac4836c5ff59b27f63e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157634"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity&gt; elemento (implantação do ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Contém informações sobre o editor que assinou o manifesto de implantação.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O `publisherIdentity` elemento é necessário para manifestos assinados. A tabela a seguir mostra os atributos que o `publisherIdentity` dá suporte ao elemento.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`name`|Necessário. Descreve a identidade da parte que publicou este aplicativo.|  
|`issuerKeyHash`|Necessário. Contém o hash SHA-1 da chave pública do emissor do certificado.|  
  
#### <a name="parameters"></a>Parâmetros  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
  
## <a name="subhead"></a>Subtítulo

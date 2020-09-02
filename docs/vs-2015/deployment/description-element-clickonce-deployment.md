---
title: '&lt;&gt;elemento Description (implantação do ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cadf4a0b525e5603247748edd63516dc26d8a0b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187753"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;&gt;elemento Description (implantação do ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifica as informações do aplicativo usadas para criar uma presença de shell e um item **Adicionar ou remover programas** no painel de controle.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O `description` elemento é obrigatório e está no `urn:schemas-microsoft-com:asm.v1` namespace. Ele não contém nenhum elemento filho e tem os atributos a seguir.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`publisher`|Obrigatórios. Identifica o nome da empresa usado para o posicionamento do ícone no menu **Iniciar** do Windows e o item **Adicionar ou remover programas** no painel de controle, quando a implantação é configurada para instalação.|  
|`product`|Obrigatórios. Identifica o nome completo do produto. Usado como o título do ícone instalado no menu **Iniciar** do Windows.|  
|`suiteName`|Opcional. Identifica uma subpasta dentro da `publisher` pasta no menu **Iniciar** do Windows.|  
|`supportUrl`|Opcional. Especifica uma URL de suporte que é mostrada no item **Adicionar ou remover programas** no painel de controle. Um atalho para essa URL também é criado para suporte a aplicativos no menu **Iniciar** do Windows, quando a implantação é configurada para instalação.|  
  
## <a name="remarks"></a>Comentários  
 O elemento Description é necessário em todas as configurações de implantação.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir ilustra um `description` elemento em um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto de implantação. Este exemplo de código faz parte de um exemplo maior fornecido para o tópico [manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md) .  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)

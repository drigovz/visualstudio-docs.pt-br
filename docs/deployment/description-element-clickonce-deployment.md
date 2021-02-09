---
title: '&lt;&gt;elemento Description (implantação do ClickOnce) | Microsoft Docs'
description: O elemento Description identifica as informações do aplicativo usadas para criar uma presença de shell e um item Adicionar ou remover programas no painel de controle.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8dee33fca027ce47ede8315f7956479ee2394382
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893081"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;&gt;elemento Description (implantação do ClickOnce)
Identifica as informações do aplicativo usadas para criar uma presença de shell e um item **Adicionar ou remover programas** no painel de controle.

## <a name="syntax"></a>Sintaxe

```xml

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
|`product`|Obrigatório. Identifica o nome completo do produto. Usado como o título do ícone instalado no menu **Iniciar** do Windows.|
|`suiteName`|Opcional. Identifica uma subpasta dentro da `publisher` pasta no menu **Iniciar** do Windows.|
|`supportUrl`|Opcional. Especifica uma URL de suporte que é mostrada no item **Adicionar ou remover programas** no painel de controle. Um atalho para essa URL também é criado para suporte a aplicativos no menu **Iniciar** do Windows, quando a implantação é configurada para instalação.|

## <a name="remarks"></a>Comentários
 O elemento Description é necessário em todas as configurações de implantação.

## <a name="example"></a>Exemplo
 O exemplo de código a seguir ilustra um `description` elemento em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto de implantação. Este exemplo de código faz parte de um exemplo maior fornecido para o tópico [manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md) .

```xml
<description
  asmv2:publisher="My Company Name"
  asmv2:product="My Application"
  xmlns="urn:schemas-microsoft-com:asm.v1" />
```

## <a name="see-also"></a>Consulte também
- [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)
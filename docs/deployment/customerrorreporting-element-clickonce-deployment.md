---
title: '&lt;&gt;elemento customErrorReporting (implantação do ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d42bd1f7304d9f50b6334d9ac8ddd4f626605d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62900365"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;&gt;elemento customErrorReporting (implantação do ClickOnce)
Especifica um URI para mostrar quando ocorre um erro.

## <a name="syntax"></a>Sintaxe

```xml
<customErrorReporting
   uri
/>
```

## <a name="remarks"></a>Comentários
 Esse elemento é opcional. Sem ele, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] exibe uma caixa de diálogo de erro mostrando a pilha de exceção. Se o `customErrorReporting` elemento estiver presente, ele [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] exibirá o URI indicado pelo `uri` parâmetro. O URI de destino incluirá a classe de exceção externa, a classe de exceção interna e a mensagem de exceção interna como parâmetros.

 Use este elemento para adicionar a funcionalidade de relatório de erros ao seu aplicativo. Como o URI gerado inclui informações sobre o tipo de erro, seu site pode analisar essas informações e exibir, por exemplo, uma tela de solução de problemas apropriada.

## <a name="example"></a>Exemplo
 O trecho a seguir mostra o `customErrorReporting` elemento, junto com o URI gerado que ele pode produzir.

```xml
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />

Example Generated Error:
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.
```

## <a name="see-also"></a>Confira também
- [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)
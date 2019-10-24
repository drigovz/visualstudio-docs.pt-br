---
title: Fornecendo automação para o código | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 874446aa6bf2e40a120aac49e7d91fd3d861d1d4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724970"
---
# <a name="providing-automation-for-code"></a>Fornecendo automação de código
Não é necessário criar um modelo de automação para seu código. O SDK do ambiente não fornece um exemplo para fazer isso. Para obter informações sobre modelos de código, consulte o objeto <xref:EnvDTE.CodeModel>.

 Para implementar um modelo de código, você deve implementar todas as interfaces que são determinadas pela sua estrutura de dados interna. Os objetos devem ser derivados da classe `IDispatch`.

 Os objetos que você estende, <xref:EnvDTE.CodeModel> e <xref:EnvDTE.FileCodeModel>, estão disponíveis no objeto <xref:EnvDTE.Project> e se parecem com o seguinte:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Você pode optar por implementar apenas o `CodeModel` ou a interface `FileCodeModel` no objeto retornado de seus objetos `Project` e <xref:EnvDTE.ProjectItem>. Forneça qualquer funcionalidade dessa interface que seja apropriada para seu sistema de projeto.

 Se você quiser adicionar recursos, como métodos ou propriedades, que não estão disponíveis nas interfaces padrão `CodeModel` e `FileCodeModel`, crie sua própria interface que herda do padrão. Certifique-se de documentá-lo com seu sistema de projeto para que os usuários finais saibam que procurar por ele. Você retorna a interface padrão, mas o usuário pode chamar o método `QueryInterface` ou converter para sua interface, se for conhecido como existir.

## <a name="see-also"></a>Consulte também
- [Visão geral do modelo de automação](../../extensibility/internals/automation-model-overview.md)
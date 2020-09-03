---
title: Fornecendo automação para o código | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd13b7db2065069ff1540dbfc921570c2b230b8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705988"
---
# <a name="providing-automation-for-code"></a>Fornecendo automação de código
Não é necessário criar um modelo de automação para seu código. O SDK do ambiente não fornece um exemplo para fazer isso. Para obter informações sobre modelos de código, consulte o <xref:EnvDTE.CodeModel> objeto.

 Para implementar um modelo de código, você deve implementar todas as interfaces que são determinadas pela sua estrutura de dados interna. Os objetos devem ser derivados da `IDispatch` classe.

 Os objetos que você estende <xref:EnvDTE.CodeModel> e <xref:EnvDTE.FileCodeModel> estão disponíveis do <xref:EnvDTE.Project> objeto e são semelhantes ao seguinte:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Você pode optar por implementar apenas o `CodeModel` ou a `FileCodeModel` interface no objeto retornado de seus `Project` <xref:EnvDTE.ProjectItem> objetos e. Forneça qualquer funcionalidade dessa interface que seja apropriada para seu sistema de projeto.

 Se você quiser adicionar recursos, como métodos ou propriedades, que não estão disponíveis no padrão `CodeModel` e nas `FileCodeModel` interfaces, crie sua própria interface que herda do padrão. Certifique-se de documentá-lo com seu sistema de projeto para que os usuários finais saibam que procurar por ele. Você retorna a interface padrão, mas o usuário pode chamar o `QueryInterface` método ou converter para sua interface, se for conhecido como existir.

## <a name="see-also"></a>Confira também
- [Visão geral do modelo de automação](../../extensibility/internals/automation-model-overview.md)

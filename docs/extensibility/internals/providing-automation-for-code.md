---
title: Fornecendo automação para código | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705988"
---
# <a name="providing-automation-for-code"></a>Fornecendo automação de código
A criação de um modelo de automação para o seu código não é necessária. O Ambiente SDK não fornece uma amostra para fazê-lo. Para obter informações sobre <xref:EnvDTE.CodeModel> modelos de código, consulte o objeto.

 Para implementar um modelo de código, você deve implementar quaisquer interfaces determinadas pela sua estrutura de dados interna. Os objetos devem ser `IDispatch` derivados da classe.

 Os objetos que <xref:EnvDTE.CodeModel> <xref:EnvDTE.FileCodeModel>você estende e <xref:EnvDTE.Project> , estão disponíveis a partir do objeto, e se parecem com o seguinte:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Você pode optar por `CodeModel` implementar `FileCodeModel` apenas a ou a `Project` <xref:EnvDTE.ProjectItem> interface no objeto que você retorna de seus objetos. Forneça qualquer funcionalidade desta interface apropriada para o seu sistema de projeto.

 Se você quiser adicionar recursos, como métodos ou propriedades, `CodeModel` que `FileCodeModel` não estão disponíveis a partir do padrão e interfaces, crie sua própria interface que herda do padrão. Certifique-se de documentá-lo com o seu sistema de projeto para que os usuários finais saibam procurá-lo. Você retorna a interface padrão, mas `QueryInterface` o usuário pode chamar o método ou lançar para sua interface se for conhecido que exista.

## <a name="see-also"></a>Confira também
- [Visão geral do modelo de automação](../../extensibility/internals/automation-model-overview.md)

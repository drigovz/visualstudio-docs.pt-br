---
title: Lista de objetos da janela de propriedades | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffe11ae6ebb4e692686c884b663a4f93d1466535
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706143"
---
# <a name="properties-window-object-list"></a>Lista de objetos de janela Propriedades
A lista de **objetos** na janela Propriedades é uma lista gota que permite alterar a seleção para outros objetos disponíveis em uma ou mais janelas selecionadas. Selecionar um objeto diferente de dentro desta <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> lista aciona uma chamada para informar o ambiente de que um novo objeto foi selecionado. As informações exibidas na janela **Propriedades** são então alteradas para mostrar as propriedades associadas ao objeto recém-selecionado.

## <a name="the-object-list"></a>A lista de objetos
 A lista de objetos consiste em dois campos: o nome do objeto (exibido em negrito) e o tipo de objeto.

 O nome do objeto exibido à esquerda do tipo de objeto em `Name` negrito é <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> recuperado do próprio objeto usando a propriedade fornecida pela interface. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, o único <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>método <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> em , retorna para a coclasse dessa interface. A **Properties** janela <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> Propriedades é usa para obter o nome da coclasse, que é exibida como o nome do objeto na lista suspensa.

 Se o objeto não `Name` tiver uma propriedade, um nome não será exibido na área Nome da lista de objetos. Você pode adicionar uma propriedade Nome ao objeto se quiser que o nome seja exibido na lista de objetos.

 Se o objeto COM <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>não for implementado, a janela **Propriedades** exibirá o nome da interface no lugar do nome do objeto no lado esquerdo da lista.

## <a name="see-also"></a>Confira também
- [Estendendo propriedades](../../extensibility/internals/extending-properties.md)

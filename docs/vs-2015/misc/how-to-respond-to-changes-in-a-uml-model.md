---
title: 'Como: responder a alterações em um modelo UML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: f0300371-9cac-4def-a3f5-7d7b62dcd6f3
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eff43f3c7547a46b75885448999335637e9fbc62
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609801"
---
# <a name="how-to-respond-to-changes-in-a-uml-model"></a>Como responder a alterações em um modelo UML
É possível escrever código que é executado sempre que uma alteração ocorre em um modelo UML no Visual Studio. Ele responderá igualmente a alterações feitas diretamente pelo usuário e por outras extensões do Visual Studio. Para ver quais versões do Visual Studio oferecem suporte a modelos UML, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!WARNING]
> Essas técnicas não são suportadas pela API UML. Eles podem não funcionar em versões futuras do Visual Studio.

 O código de exemplo está disponível em [UML: respondendo a alterações em um modelo UML usando eventos e regras](http://code.msdn.microsoft.com/UML-Responding-to-changes-c024cd4b)

## <a name="see-also"></a>Consulte também
 Navegar pelos manipuladores [de eventos de modelo UML](../modeling/navigate-the-uml-model.md) [propagar alterações fora do exemplo de modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md) [: cor por estereótipo](http://go.microsoft.com/fwlink/?LinkId=213841)
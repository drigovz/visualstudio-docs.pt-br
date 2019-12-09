---
title: Anexar cadeias de caracteres de referência a elementos de modelo UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending, reference strings
ms.assetid: 15dbed99-efce-42fe-a768-714a5804e7d1
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7726379258ef474b57f1ca4a924413cd93cf80bb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672785"
---
# <a name="attach-reference-strings-to-uml-model-elements"></a>Anexar cadeias de caracteres de referência a elementos de modelo UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode escrever código para anexar cadeias de caracteres arbitrárias a elementos de modelo. Uma cadeia de caracteres poderia ser, por exemplo, um URI, o resultado em cache de uma computação ou uma referência ModelBus a um elemento em outro modelo. Cada cadeia de caracteres está contida em um objeto IReference. Qualquer número de objetos IReference pode ser anexado a cada elemento de modelo.

 Cada objeto IReference tem um nome. Você pode usar esse nome para indicar como o valor de referência deve ser interpretado. Por exemplo, você pode definir o nome como "URI" para indicar que o valor deve ser interpretado como um URI. Há alguns valores de nome de referência predefinidos usados pelas ferramentas de modelagem.

## <a name="attaching-a-reference-to-an-ielement"></a>Anexando uma referência a um ielemento
 Para usar os métodos a seguir, você deve adicionar uma referência a:

 Microsoft. VisualStudio. ArchitectureTools. Extensibility. dll

 Você deve inserir essa diretiva em seu código:

 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`

|Chamada de método|Descrição|
|-----------------|-----------------|
|`element.AddReference (nameString, valueString, duplicatesAllowed)`|Cria um `IReference` com as cadeias de caracteres de nome e valor fornecidas e vincula-o a `element`. Retorna o `IReference`.<br /><br /> Gera uma exceção se `duplicatesAllowed` for false e já houver um `IReference` com o mesmo nome anexado a `element`.|
|`element.GetReferences(name)`|Retorna todos os objetos de `IReference` vinculados a `element` que têm o `name` especificado.|
|`element.DeleteAllReferences(name)`|Exclui todos os objetos de `IReference` vinculados ao elemento que têm o nome fornecido.|
|`reference.Delete()`|Exclui este `IReference`.|
|`ReferenceConstants.WorkItem`|O valor usado para nomear referências de item de trabalho.|

## <a name="see-also"></a>Consulte também
 [Definir um manipulador de link de item de trabalho](../modeling/define-a-work-item-link-handler.md) [definir e instalar uma programação de extensão de modelagem](../modeling/define-and-install-a-modeling-extension.md) [com a API UML](../modeling/programming-with-the-uml-api.md)

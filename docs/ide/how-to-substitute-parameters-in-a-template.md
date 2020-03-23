---
title: Adicionar parâmetros de nome a modelos de projeto e de item
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 9ddfe065d30b958e52e22f30f946d01d626fcf0e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591405"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Como substituir parâmetros em um modelo

Os parâmetros de modelo permitem que você substitua identificadores como nomes de classe e namespaces quando um arquivo é criado com base em um modelo. Você pode adicionar parâmetros de modelo em modelos existentes ou criar seus próprios modelos com os parâmetros de modelo.

Parâmetros de modelo são escritos no formato $*parâmetro*$. Para obter uma lista completa dos parâmetros de modelo, consulte [Parâmetros de modelo](../ide/template-parameters.md).

A seção a seguir mostra como modificar um modelo para substituir o nome de um namespace pelo "nome seguro do projeto".

## <a name="example---namespace-name"></a>Exemplo – o nome do namespace

1. Insira o parâmetro em um ou mais dos arquivos de código no modelo. Por exemplo: 

    ```csharp
    namespace $safeprojectname$
    ```

1. No arquivo *vstemplate* para o `ProjectItem` modelo, localize o elemento que inclui este arquivo.

1. Defina o atributo `ReplaceParameters` como `true` para o elemento `ProjectItem`:

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Confira também

- [Criar modelos de projeto e itens](../ide/creating-project-and-item-templates.md)
- [Parâmetros de modelo](../ide/template-parameters.md)
- [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Elemento ProjectItem (modelos de itens do Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)

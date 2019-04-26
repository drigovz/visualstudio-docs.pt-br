---
title: Adicionar parâmetros de nome a modelos de projeto e de item
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cf9a990be3f5e87180967a4f9f274ec79fbc357e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946865"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Como: Substituir parâmetros em um modelo

Os parâmetros de modelo permitem que você substitua identificadores como nomes de classe e namespaces quando um arquivo é criado com base em um modelo. Você pode adicionar parâmetros de modelo em modelos existentes ou criar seus próprios modelos com os parâmetros de modelo.

Parâmetros de modelo são escritos no formato $*parâmetro*$. Para obter uma lista completa dos parâmetros de modelo, consulte [Parâmetros de modelo](../ide/template-parameters.md).

A seção a seguir mostra como modificar um modelo para substituir o nome de um namespace pelo "nome seguro do projeto".

## <a name="example---namespace-name"></a>Exemplo – o nome do namespace

1. Insira o parâmetro em um ou mais dos arquivos de código no modelo. Por exemplo:

    ```csharp
    namespace $safeprojectname$
    ```

1. No arquivo *vstemplate* do modelo, localize o elemento `ProjectItem` que inclui esse arquivo.

1. Defina o atributo `ReplaceParameters` como `true` para o elemento `ProjectItem`:

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Consulte também

- [Criar modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
- [Parâmetros de modelo](../ide/template-parameters.md)
- [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Elemento ProjectItem (modelos de item do Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
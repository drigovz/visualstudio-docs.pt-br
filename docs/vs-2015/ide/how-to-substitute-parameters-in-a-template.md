---
title: Como substituir parâmetros em um modelo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- template parameters, substituting
- Visual Studio templates, using parameters
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fe49c928ca3de318410eba56afeae6f4329efed3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670655"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Como substituir parâmetros em um modelo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode substituir parâmetros de modelo, como nomes de classes e namespaces, quando um arquivo baseado em um modelo for criado. Para obter uma lista completa de parâmetros de modelo, consulte [parâmetros de modelo](../ide/template-parameters.md).

## <a name="procedure"></a>Procedimento
 Você pode substituir parâmetros nos arquivos de um modelo sempre que um projeto baseado nesse modelo for criado. Este procedimento explica como criar um modelo que substitui o nome de um namespace pelo nome do projeto seguro quando um novo projeto for criado com o modelo.

#### <a name="to-use-a-parameter-to-replace-namespace-name-with-the-project-name"></a>Para usar um parâmetro para substituir o nome do namespace pelo nome do projeto

1. Insira o parâmetro em um ou mais dos arquivos de código no modelo. Por exemplo:

    ```
    namespace $safeprojectname$
    ```

    > [!NOTE]
    > Parâmetros de modelo são escritos no formato $*parâmetro*$.

2. No arquivo .vstemplate do modelo, localize o elemento `ProjectItem` que inclui esse arquivo.

3. Defina o atributo `ReplaceParameters` como `true` para o elemento `ProjectItem`. Por exemplo:

    ```
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Consulte Também
 [Criando modelos de modelo de projeto e item](../ide/creating-project-and-item-templates.md) [parâmetros de template](../ide/template-parameters.md) [referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md) [elemento ProjectItem (modelos de item do Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)

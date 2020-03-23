---
title: Tarefa XSD | Microsoft Docs
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.xsd
- VC.Project.VCXMLDataGeneratorTool.Namespace
- VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XSD task (MSBuild (C++))
- MSBuild (C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 217e045a731efa1fe3ba1dda63e89eca685d4b75
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630776"
---
# <a name="xsd-task"></a>tarefa XSD

Envolve a ferramenta XML Schema Definition *(xsd.exe),* que gera esquemas ou arquivos de classe a partir de uma fonte.

> [!NOTE]
> A partir do Visual Studio 2017, o suporte a projetos em C++ para *xsd.exe* foi preterido. Você ainda pode usar as APIs **Microsoft.VisualC.CppCodeProvider** manualmente adicionando *CppCodeProvider.dll* ao cache de assembly global.

## <a name="parameters"></a>parâmetros

 A tabela a seguir descreve os parâmetros da tarefa **XSD**.

- **AdditionalOptions**

     Parâmetro opcional **string.**

     Uma lista de opções, conforme especificado na linha de comando. Por exemplo, /\<option1> /\<option2> /\<option#>. Use esse parâmetro para especificar opções não representadas por nenhum outro parâmetro da tarefa **XSD**.

- **GenerateFromSchema**

  Parâmetro opcional **string.**

  Especifica os tipos gerados com base no esquema especificado.

  Especifique um dos valores a seguir, cada um dos quais correspondente a uma opção XSD.

  - **classes** - **/classes**

  - **conjunto de** - dados **/conjunto de dados**

- **Língua**

     Parâmetro opcional **string.**

     Especifica a linguagem de programação a ser usada para o código gerado.

     Escolha **CS** (C#, que é o padrão), **VB** (Visual Basic) ou **JS** (JScript). Você também pode especificar um nome totalmente qualificado para uma classe que implementa `System.CodeDom.Compiler.CodeDomProvider Class`

- **Namespace**

     Parâmetro opcional **string.**

     Especifica o namespace de runtime para os tipos gerados.

- **Fontes**

     Parâmetro `ITaskItem[]` obrigatório.

     Define uma matriz de itens de arquivo de origem do MSBuild que pode ser consumida e emitida por tarefas.

- **SuppressStartupBanner**

     Parâmetro **booleano** opcional.

     Se `true`, impedirá a exibição da mensagem de direitos autorais e de número de versão quando a tarefa for iniciada.

- **TrackerLogDirectory**

     Parâmetro opcional **string.**

     Especifica o diretório do log de rastreamento.

## <a name="see-also"></a>Confira também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)

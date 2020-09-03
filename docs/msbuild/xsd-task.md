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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77630776"
---
# <a name="xsd-task"></a>tarefa XSD

Encapsula a ferramenta de definição de esquema XML (*xsd.exe*), que gera arquivos de esquema ou classe de uma origem.

> [!NOTE]
> A partir do Visual Studio 2017, o suporte a projetos em C++ para *xsd.exe* foi preterido. Você ainda pode usar as APIs **Microsoft.VisualC.CppCodeProvider** manualmente adicionando *CppCodeProvider.dll* ao cache de assembly global.

## <a name="parameters"></a>Parâmetros

 A tabela a seguir descreve os parâmetros da tarefa **XSD**.

- **AdditionalOptions**

     Parâmetro de **cadeia de caracteres** opcional.

     Uma lista de opções, conforme especificado na linha de comando. Por exemplo,/ \<option1>  / \<option2>  / \<option#> . Use esse parâmetro para especificar opções não representadas por nenhum outro parâmetro da tarefa **XSD**.

- **GenerateFromSchema**

  Parâmetro de **cadeia de caracteres** opcional.

  Especifica os tipos gerados com base no esquema especificado.

  Especifique um dos valores a seguir, cada um dos quais correspondente a uma opção XSD.

  - **classes**  -  do **/classes**

  - **conjunto**  -  de **/DataSet**

- **Idioma**

     Parâmetro de **cadeia de caracteres** opcional.

     Especifica a linguagem de programação a ser usada para o código gerado.

     Escolha **CS** (C#, que é o padrão), **VB** (Visual Basic) ou **JS** (JScript). Você também pode especificar um nome totalmente qualificado para uma classe que implementa `System.CodeDom.Compiler.CodeDomProvider Class`

- **Namespace**

     Parâmetro de **cadeia de caracteres** opcional.

     Especifica o namespace de runtime para os tipos gerados.

- **Fontes**

     Parâmetro `ITaskItem[]` obrigatório.

     Define uma matriz de itens de arquivo de origem do MSBuild que pode ser consumida e emitida por tarefas.

- **SuppressStartupBanner**

     Parâmetro **booliano** opcional.

     Se `true`, impedirá a exibição da mensagem de direitos autorais e de número de versão quando a tarefa for iniciada.

- **TrackerLogDirectory**

     Parâmetro de **cadeia de caracteres** opcional.

     Especifica o diretório do log de rastreamento.

## <a name="see-also"></a>Confira também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)

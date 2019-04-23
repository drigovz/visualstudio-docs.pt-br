---
title: Tarefa de aviso | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Warning
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Warning task [MSBuild]
- MSBuild, Warning task
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: adbddc2fb36e5036e535dfc1049945187fe14ed0
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59667788"
---
# <a name="warning-task"></a>Tarefa Warning
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Registra um aviso durante um build com base em uma instrução condicional avaliada.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `Warning`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`Code`|Parâmetro `String` opcional.<br /><br /> O código de erro que será associado ao aviso.|  
|`File`|Parâmetro `String` opcional.<br /><br /> Especifica o arquivo relevante, se houver. Se nenhum arquivo for fornecido, o arquivo que contém a tarefa de aviso será usado.|  
|`HelpKeyword`|Parâmetro `String` opcional.<br /><br /> A palavra-chave Ajuda que será associada ao aviso.|  
|`Text`|Parâmetro `String` opcional.<br /><br /> O texto de aviso que [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] registra se o parâmetro `Condition` resultar em `true`.|  
  
## <a name="remarks"></a>Comentários  
 A tarefa `Warning` permite que projetos [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] verifiquem a presença de uma configuração necessária ou propriedade antes de continuar com a próxima etapa de build.  
  
 Se o parâmetro `Condition` da tarefa `Warning` for avaliada como `true`, o valor do parâmetro `Text` será registrado e o build continuará a ser executada. Se um parâmetro `Condition` não existir, o texto de aviso será registrado. Para obter mais informações sobre registro, consulte [Obter logs de build](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir verifica as propriedades que são definidas na linha de comando. Se nenhuma propriedade estiver definida, o projeto gerará um evento de aviso e registrará o valor do parâmetro `Text` da tarefa `Warning`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Warning  
            Text=" The 0 property was not set on the command line."  
            Condition="'$(0)' == ''" />  
        <Warning  
            Text=" The FREEBUILD property was not set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Obtaining Build Logs (Obtendo logs de build)](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)

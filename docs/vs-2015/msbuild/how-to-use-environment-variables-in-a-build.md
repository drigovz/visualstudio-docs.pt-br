---
title: 'Como: Usar variáveis de ambiente em um build | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 40b296e33d00e6abf6730c7ec29a1fe9ed8e039b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60067983"
---
# <a name="how-to-use-environment-variables-in-a-build"></a>Como: Usar variáveis de ambiente em um build
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando você compila projetos, geralmente é necessário definir opções de build usando informações que não estão no arquivo de projeto ou nos arquivos que compõem seu projeto. Normalmente, essas informações são armazenadas em variáveis de ambiente.  
  
## <a name="referencing-environment-variables"></a>Fazendo referência a variáveis de ambiente  
 Todas as variáveis de ambiente estão disponíveis para o arquivo de projeto [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ([!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]) como propriedades.  
  
> [!NOTE]
>  Se o arquivo de projeto contiver uma definição explícita de uma propriedade que tem o mesmo nome que uma variável de ambiente, a propriedade no arquivo de projeto substituirá os valores de uma variável de ambiente.  
  
#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>Para usar uma variável de ambiente em um projeto MSBuild  
  
- Faça referência à variável de ambiente da mesma maneira que faria com uma variável declarada em seu arquivo de projeto. Por exemplo, o código a seguir faz referência à variável de ambiente BIN_PATH:  
  
   `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`  
  
  Você pode usar um atributo `Condition` para fornecer um valor padrão para uma propriedade se a variável de ambiente não foi definida.  
  
#### <a name="to-provide-a-default-value-for-a-property"></a>Para fornecer um valor padrão de uma propriedade  
  
- Use um atributo `Condition` em uma propriedade para definir o valor somente se a propriedade não tiver nenhum valor. Por exemplo, o código a seguir definirá a propriedade `ToolsPath` como c:\Tools somente se a variável de ambiente `ToolsPath` não estiver definida:  
  
     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`  
  
    > [!NOTE]
    >  Os nomes de propriedade não diferenciam maiúsculas de minúsculas então `$(ToolsPath)` e `$(TOOLSPATH)` fazem referência à mesma variável de ambiente ou propriedade.  
  
## <a name="example"></a>Exemplo  
 O arquivo de projeto a seguir usa variáveis de ambiente para especificar o local dos diretórios.  
  
```  
<Project DefaultTargets="FakeBuild">  
    <PropertyGroup>  
        <FinalOutput>$(BIN_PATH)\myassembly.dll</FinalOutput>  
        <ToolsPath Condition=" '$(ToolsPath)' == '' ">  
            C:\Tools  
        </ToolsPath>  
    </PropertyGroup>  
    <Target Name="FakeBuild">  
        <Message Text="Building $(FinalOutput) using the tools at $(ToolsPath)..."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Consulte também  

[MSBuild](msbuild.md)

[Propriedades MSBuild](../msbuild/msbuild-properties1.md)

[Como: Compilar os mesmos arquivos de origem com opções diferentes](../msbuild/how-to-build-the-same-source-files-with-different-options.md)

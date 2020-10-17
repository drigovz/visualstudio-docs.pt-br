---
title: Ações de build para arquivos
description: Saiba como todos os arquivos em um projeto do Visual Studio têm uma ação de compilação e a ação de compilação controla o que acontece com o arquivo quando o projeto é compilado.
ms.custom: SEO-VS-2020
ms.date: 11/19/2018
ms.technology: vs-ide-compile
ms.topic: reference
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8884eaa459fa3a2a7dd8d10f0ffeca5003398afd
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136726"
---
# <a name="build-actions"></a>Ações de Build

Todos os arquivos em um projeto do Visual Studio têm uma ação de build. A ação de build controla o que acontece com o arquivo quando o projeto é compilado.

> [!NOTE]
> Este tópico aplica-se ao Visual Studio no Windows. Para o Visual Studio para Mac, confira [Build actions in Visual Studio for Mac](/visualstudio/mac/build-actions) (Ações de build no Visual Studio para Mac).

## <a name="set-a-build-action"></a>Definir uma ação de build

Para definir a ação de build para um arquivo, abra as propriedades do arquivo na janela **Propriedades** selecionando o arquivo no **Gerenciador de Soluções** e pressionando **Alt**+**Enter**. Ou clique com o botão direito do mouse no arquivo no **Gerenciador de Soluções** e escolha **Propriedades**. Na janela **Propriedades**, na seção **Avançado**, use a lista suspensa ao lado de **Ação de Build** para definir uma ação de build para o arquivo.

![Ações de build para um arquivo no Visual Studio](media/build-actions.png)

## <a name="build-action-values"></a>Valores de ação de build

Algumas das ações de build mais comuns para arquivos de projeto do C# e Visual Basic são:

|Criar ação | Tipos de projeto | Descrição |
|-|-|
| **AdditionalFiles** | C#, Visual Basic | Um arquivo de texto que não seja de origem passado para o compilador do C# ou do Visual Basic como entrada. Essa ação de build é usada principalmente para fornecer entradas para [analisadores](../code-quality/roslyn-analyzers-overview.md) referenciados por um projeto para verificar a qualidade do código. Para obter mais informações, confira [Usar arquivos adicionais](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md).|
| **ApplicationDefinition** | WPF | O arquivo que define seu aplicativo. Ao criar um projeto pela primeira vez, ele é *App.xaml*. |
| **CodeAnalysisDictionary** | .NET | Um dicionário de palavras personalizado, usado pela Análise de Código para verificação ortográfica. Consulte [como: personalizar o dicionário de análise de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)|
| **Compilar** | any | O arquivo é passado para o compilador como um arquivo de origem.|
| **Conteúdo** | .NET | Um arquivo marcado como **Content** pode ser recuperado como um fluxo chamando <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType>. Para projetos ASP.NET, esses arquivos são incluídos como parte do site quando ele for implantado.|
| **DesignData** | WPF | Usado para arquivos ViewModel do XAML, para permitir que os controles do usuário sejam visualizados em tempo de design, com tipos e dados de amostra fictícios. |
| **DesignDataWithDesignTimeCreateable** | WPF | Como o **DesignData**, mas com tipos reais.  |
| **Embedded Resource** | .NET | O arquivo é passado para o compilador como um recurso a ser inserido no assembly. É possível chamar <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> para ler o arquivo do assembly.|
| **EntityDeploy** | .NET | Para arquivos .edmx do Entity Framework (EF) que especificam a implantação de artefatos do EF. |
| **Fakes** | .NET | Usado para a estrutura de testes do Microsoft Fakes. Confira [Isolar o código em teste com o Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) |
| **Nenhuma** | any | O arquivo não faz parte do build de nenhuma maneira. Esse valor pode ser usado para arquivos de documentação como "Leiame", por exemplo.|
| **Página** | WPF | Compile um arquivo XAML em um arquivo. BAML binário para um carregamento mais rápido em tempo de execução. |
| **Recurso** | WPF | Especifica a inserção do arquivo em um arquivo de recursos do manifesto do assembly com a extensão *.g.resources*. |
| **Shadow** | .NET | Usado para um arquivo .accessor que contém uma lista de nomes de arquivos do assembly inseridos, um por linha. Para cada assembly na lista, gere classes públicas com os nomes `ClassName_Accessor` que são exatamente como os originais, mas com métodos públicos ao invés de métodos privados. Usado para teste de unidade. |
| **Tela inicial** | WPF | Especifica um arquivo de imagem a ser exibido em tempo de execução quando o aplicativo estiver sendo inicializado. |
| **XamlAppDef** | Windows Workflow Foundation | Instrui a compilação a criar um arquivo XAML de fluxo de trabalho em um assembly com um fluxo de trabalho inserido. |

> [!NOTE]
> Ações adicionais de build podem ser definidas por tipos de projeto específicos, portanto, a lista de ações de build depende do tipo de projeto, e podem aparecer valores que não estão nessa lista.

## <a name="see-also"></a>Confira também

- [Opções do compilador C#](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Opções do compilador do Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [Ações de build (Visual Studio para Mac)](/visualstudio/mac/build-actions)

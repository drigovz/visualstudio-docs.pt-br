---
title: Opções, Editor de Texto, C#, Avançado
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 16c92111fc29071447d4af5e736b881fa7c7a769
ms.sourcegitcommit: e680e8ac675f003ebcc8f8c86e27f54ff38da662
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356737"
---
# <a name="options-text-editor-c-advanced"></a>Opções, Editor de Texto, C#, Avançado

Use a página de opções **Avançado** para modificar as configurações de formatação do editor, de refatoração de código e de comentários da documentação XML para C#. Para acessar essa página de opções, escolha **Ferramentas** > **Opções** e, em seguida, **Editor de Texto** > **C#** > **Avançado**.

> [!NOTE]
> É possível que nem todas as opções estejam listadas aqui.

## <a name="analysis"></a>Análise

- Habilitar análise de solução completa

   Permite a análise de código em todos os arquivos na solução, não apenas nos arquivos de código abertos. Para obter mais informações, confira [Análise de solução completa](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="using-directives"></a>Usando diretivas

- Colocar as diretivas “System” primeiro ao classificar os usos

   Quando selecionado, o comando **Remover e classificar usos** no menu de clique com o botão direito classifica as diretivas `using` e coloca os namespaces "System" no topo da lista

   Antes da classificação:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```
   
   Após a classificação:

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using AutoMapper;
   using FluentValidation;
   using Newtonsoft.Json;
   ```
   
- Separar usando grupos de diretivas

   Quando selecionado, o comando **Remover e classificar usos** no menu de clique com o botão direito do mouse separa as diretivas `using` inserindo uma linha vazia entre os grupos de diretivas que têm o mesmo namespace de raiz.

   Antes da classificação:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```
   
   Após a classificação:
   
   ```csharp
   using AutoMapper;
   
   using FluentValidation;
   
   using Newtonsoft.Json;
   
   using System;
   using System.Collections.Generic;
   using System.Linq;
   ```
   
- Adicionar usos para tipos em assemblies de referência e pacotes do NuGet 

   Quando selecionado, uma [Ação Rápida](../quick-actions.md) está disponível para instalar um pacote do NuGet e adicionar uma diretriz `using` para tipos não referenciados.

   ![Ação rápida para instalar o pacote NuGet no Visual Studio](media/nuget-lightbulb.png)
  
## <a name="highlighting"></a>Realce

- Realçar referências a símbolo sob o cursor

   Quando o cursor é posicionado em um símbolo, ou ao clicar em um símbolo, todas as instâncias desse símbolo no arquivo de código são realçadas.

## <a name="outlining"></a>Estrutura de tópicos

- Entre no modo estrutura de tópicos quando os arquivos abrem

   Quando selecionado, descreve o arquivo de código automaticamente, o que cria blocos de código recolhíveis. Na primeira vez que um arquivo é aberto, blocos #regions e blocos de códigos inativos são recolhidos.

## <a name="editor-help"></a>Ajuda do Editor

- Gerar comentários da documentação XML para ///

   Quando selecionado, insere os elementos XML dos comentários da documentação XML depois que você digita a introdução de comentário `///`. Para obter mais informações sobre a documentação XML, confira [Comentários da documentação XML (Guia de Programação em C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

## <a name="see-also"></a>Consulte também

- [Como inserir comentários XML para geração de documentação](../../ide/reference/generate-xml-documentation-comments.md)
- [Comentários de documentação XML (Guia de Programação em C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Documentar o código com comentários XML (guia do C#)](/dotnet/csharp/codedoc)
- [Definir opções de editor específicas a um idioma](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)

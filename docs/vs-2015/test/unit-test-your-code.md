---
title: Efetuar teste de unidade em seu código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.assetid: c191de3e-3f3b-471e-b828-29ec24e80e2c
caps.latest.revision: 64
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7a8b9a4b52fce5fb838c12ccf057fd0e80619cd7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851254"
---
# <a name="unit-test-your-code"></a>Teste de unidade de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os testes de unidade fornecem aos desenvolvedores e testadores uma maneira rápida de procurar por erros lógicos nos métodos de classes em projetos do [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)], do [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)] e do [!INCLUDE[cpp_current_short](../includes/cpp-current-short-md.md)].

 As ferramentas de testes de unidade incluem:

1. **Gerenciador de testes.** O Gerenciador de Testes permite realizar testes de unidade e exibir seus resultados. O Gerenciador de Testes pode usar qualquer framework de teste de unidade, incluindo framework de terceiros, que tenha um adaptador para o Explorer.

2. **Framework de teste de unidade da Microsoft para código gerenciado.** O framework de testes de unidade da Microsoft para código gerenciado é instalado com o Visual Studio e fornece um framework para testar o código .NET.

3. **Framework de teste de unidade da Microsoft para C++.** O framework de testes de unidade da Microsoft para C++ é instalado com o Visual Studio e fornece um framework para testar o código nativo.

4. **Ferramentas de cobertura de código.** É possível determinar a quantidade de código do produto que seus testes de unidade utilizam com um comando no Gerenciador de Testes.

5. **Framework de isolamento do Microsoft Fakes.** O framework de isolamento do Microsoft Fakes pode criar classes e métodos substitutos para o código de produção e de sistema que criam dependências do código em teste. Ao implementar os delegados falsos para uma função, você controla o comportamento e a saída do objeto de dependência.

   Você também pode usar o [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) para explorar seu código .NET para gerar dados de teste e um conjunto de testes de unidade. Para cada instrução no código, é gerada uma entrada de teste para executar essa instrução. Uma análise de caso é realizada para cada branch condicional do código.

## <a name="key-tasks"></a>Tarefas-chave
 Use os tópicos a seguir como auxílio para entender e criar testes de unidades:

|Tarefas|Tópicos associados|
|-----------|-----------------------|
|**Guias de início rápido e passo a passo:** use os tópicos a seguir para aprender sobre teste de unidade no Visual Studio a partir de exemplos de código.|-   [Passo a passo: criação e execução de testes de unidade para código gerenciado](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [Início Rápido: desenvolvimento controlado por teste com o Gerenciador de testes](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Adicionando testes de unidade a aplicativos C++ existentes](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)<br />-   [Código nativo de teste de unidade com o gerenciador de testes](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c)|
|**Teste de unidade com o gerenciador de testes:** saiba como o gerenciador de testes pode ajudar a criar testes de unidade mais produtivos e eficientes.|-   [Noções básicas do teste de unidade](../test/unit-test-basics.md)<br />-   [Criar um projeto de teste de unidade](../test/create-a-unit-test-project.md)<br />-   [Executar testes de unidade com o Gerenciador de testes](../test/run-unit-tests-with-test-explorer.md)<br />-   [Instalar estruturas de teste de unidade de terceiros](../test/install-third-party-unit-test-frameworks.md)<br />-   [Atualização de testes de unidade a partir do Visual Studio 2010](https://msdn.microsoft.com/9bb75856-f68a-4de2-a084-b08a947a1172)|
|**Código gerenciado de teste de unidade:**|-   [Como escrever testes de unidade para .NET Framework com o framework de teste de unidade da Microsoft para código gerenciado](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|
|**Teste de unidade de código C++**|-   [Como escrever testes de unidade para C/C++ com o framework de testes de unidade da Microsoft para C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|
|**Isolamento de testes de unidade**|-   [Isolamento de código em teste com Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Uso da cobertura de código para identificar quais proporções do código do projeto estão sendo testadas usando os testes de unidade:** saiba mais sobre o recurso de cobertura de código das ferramentas de teste do [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)].|-   [Usando a cobertura de código para determinar a quantidade de código que está sendo testada](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Execução de análise de estresse e desempenho usando testes de carga para seus testes de unidade:** você pode criar um teste de carga e adicionar seus testes de unidade a ele para ajudar a isolar os problemas de estresse e desempenho em seu aplicativo. **Nota:** a criação e utilização dos testes de carga requerem o Visual Studio Enterprise.|-   [Criação e edição de testes de carga](https://msdn.microsoft.com/e2985d15-60a7-4177-93b4-f986c2936337)<br />-   [Como: adicionar testes de desempenho na Web e testes de unidade para um cenário de teste de carga](https://msdn.microsoft.com/03cc073e-9bdf-4530-ae46-504a51884594)<br />-   [Como: remover testes da Web e testes de unidade de um cenário de teste de carga](https://msdn.microsoft.com/3d6128d2-82b0-42fc-bda2-23a8aa03be07)|
|**Definição e aplicação de restrições de qualidade:** você pode criar restrições de qualidade para garantir que os testes sejam executados antes que o código seja verificado para ajudar a garantir a qualidade do código.|-   [Definição e aplicação de restrições de qualidade](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|
|**Extensão do tipo de teste de unidade:** você pode adicionar uma funcionalidade aos seus testes que pode não estar no framework de teste de unidade. Por exemplo, é possível adicionar uma propriedade de teste que especifica se um teste deve ser executado como um usuário normal ou não. Ou você pode estender a estrutura para adicionar atributos de linha a um método e usar os dados nessa linha dentro do teste.|Para o código de exemplo de como estender o framework de teste de unidade, confira este [Site da Microsoft](https://msdn.microsoft.com/vstudio/ff420671.aspx).|
|**Definição de opções de teste:** por exemplo, você pode especificar onde os resultados dos testes são armazenados.|[Configurar testes de unidade usando um arquivo .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="related-tasks"></a>Tarefas relacionadas
 [Revisão dos resultados de testes no Microsoft Test Manager](https://msdn.microsoft.com/9fb3e429-78df-4fe2-89ed-0ad1db0738f4)

 Descreve os resultados dos testes e as maneiras de trabalhar com eles, incluindo como exibi-los, salvá-los e excluí-los.

 [Executando testes do sistema usando Microsoft Visual Studio](https://msdn.microsoft.com/library/19fae5c4-5798-4c4c-b531-3e8f901b1130)

 Fornece links para informações sobre o uso do Visual Studio em vez de usar o [!INCLUDE[TCMext](../includes/tcmext-md.md)] para executar testes automatizados.

## <a name="reference"></a>Referência
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> Descreve o namespace UnitTesting, que fornece atributos, exceções, declarações e outras classes que dão suporte ao teste de unidade.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> Descreve o namespace UnitTesting. Web, que estende o namespace UnitTesting fornecendo suporte para [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] testes de unidade de serviço da Web e.

## <a name="external-resources"></a>Recursos externos

### <a name="videos"></a>vídeos
 [Canal 9: teste de unidade dos aplicativos da Windows Store criados com XAML](https://channel9.msdn.com/Events/BUILD/BUILD2011/TOOL-529T)

### <a name="forums"></a>Fóruns
 [Teste de unidade do Visual Studio](https://social.msdn.microsoft.com/Forums/en/vsunittest/threads)

### <a name="guidance"></a>Diretrizes
 [Testes de Entrega Contínua com o Visual Studio 2012 – Capítulo 2: Teste de Unidade: Testando o Interior](https://msdn.microsoft.com/library/jj159340.aspx)

### <a name="reference"></a>Referência
 [Índice de conteúdo para testes de unidade](https://blogs.msdn.com/b/mathew_aniyan/archive/2012/05/17/content-index-for-unit-test.aspx)

## <a name="see-also"></a>Consulte Também
 [Melhorar](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945) [o teste de qualidade de código do aplicativo](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)

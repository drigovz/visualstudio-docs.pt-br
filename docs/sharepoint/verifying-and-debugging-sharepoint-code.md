---
title: Verificando e Depurando o código do SharePoint | Microsoft Docs
description: Verifique e depure o código do SharePoint. Use o IntelliTrace para examinar eventos anteriores e o estado atual em sua solução. Use o teste de unidade para garantir que seus métodos funcionem corretamente.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- unit testing [SharePoint development in Visual Studio]
- IntelliTrace [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, IntelliTrace
- SharePoint development in Visual Studio, unit testing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d406afbc0a8506262f1bdc17310802b7f41a931a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892132"
---
# <a name="verify-and-debug-sharepoint-code"></a>Verificar e depurar o código do SharePoint
Usando o IntelliTrace e o teste de unidade, você pode depurar com mais facilidade suas soluções do SharePoint e garantir que cada método delas funcione corretamente. Você pode usar esses recursos para projetos do SharePoint no Visual Studio seguindo os mesmos procedimentos que para outros tipos de projetos.

## <a name="intellitrace"></a>IntelliTrace
Usando o IntelliTrace, você pode determinar não apenas o estado atual da solução do SharePoint, mas também os eventos que ocorreram no passado e o contexto em que eles ocorreram. Você pode navegar para frente e para trás até vários pontos no tempo em sua solução do SharePoint, em que os eventos de interesse foram registrados e examinar os Estados e valores de variáveis em cada ponto. Ao usar essa navegação dinâmica, você pode depurar com mais rapidez e facilidade suas soluções do SharePoint sem precisar definir vários pontos de interrupção. Você também pode salvar a sessão de depuração em um arquivo de log do IntelliTrace (*. itrace*), abri-lo mais tarde no Visual Studio Enterprise e executar a depuração pós-Crash. O arquivo *. itrace* inclui informações detalhadas sobre quando e onde erros específicos do SharePoint ocorreram, para que você possa descobrir mais facilmente o que está causando os erros. As informações no arquivo *. itrace* são um subconjunto do log de erros completo que o sistema de log unificado (ULS) do SharePoint cria. Essas informações incluem eventos que são específicos do SharePoint, como quando um perfil de usuário é aberto ou fechado e quando as propriedades em um projeto do SharePoint são carregadas, lidas ou alteradas. Você pode configurar quais eventos o IntelliTrace registra. Para obter mais informações, consulte [usando dados do IntelliTrace salvos](../debugger/using-saved-intellitrace-data.md).

Quando ocorre um erro no SharePoint, a caixa de diálogo de erro exibe um identificador de "ID de correlação" para esse erro específico. Você também pode obter IDs de correlação de eventos listados no arquivo *. itrace* . Para exibir uma lista de todos os eventos que ocorreram com uma determinada ID de correlação, você pode inserir a ID na seção **análise** da página de resumo do IntelliTrace. Nessa seção, você pode escolher se deseja exibir somente os nomes dos eventos que ocorreram ou os nomes dos eventos, juntamente com suas informações de chamada, como o nome da função, saída e pontos de entrada, parâmetros e valores de retorno.

Você pode obter eventos do Visual Studio no IntelliTrace escolhendo a tecla **F5** . No entanto, para obter eventos específicos do SharePoint, você deve coletar dados do IntelliTrace em soluções do SharePoint usando Microsoft Monitoring Agent. Essa ferramenta coleta dados do IntelliTrace e cria arquivos *. itrace* para aplicativos que são implantados fora do Visual Studio. Para obter mais informações, consulte [recursos do IntelliTrace](../debugger/intellitrace-features.md) e [uso do coletor autônomo do IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

## <a name="unit-test"></a>Teste de unidade
Você pode encontrar mais facilmente erros em seu código executando o teste de unidade, no qual você escreve e executa o código de teste dentro de métodos de teste. Esses métodos contêm variáveis vazias e uma instrução Assert que você pode usar para verificar a lógica e a funcionalidade do seu projeto com base no modelo de objeto do SharePoint. Para obter mais informações, consulte [Efetuar teste de unidade em seu código](../test/unit-test-your-code.md).

### <a name="support-for-microsoft-fakes-framework"></a>Suporte para a estrutura de falsificações da Microsoft
Os projetos do SharePoint dão suporte a falsificações da Microsoft, que é uma estrutura de isolamento na qual você pode criar stubs de teste baseados em delegado e shims em aplicativos baseados no .NET Framework. Usando a estrutura de falsificações, você pode criar, manter e injetar implementações fictícias em seus testes de unidade. Esses stubs e shims isolam os testes de unidade do ambiente. Você pode criar stubs para o código de teste que consome interfaces ou classes não seladas com métodos substituíveis. Você pode criar shims para redirecionar chamadas embutidas em código para classes lacradas com métodos estáticos ou não substituíveis em uma implementação de Shim alternativo. Você também pode usar delegados com tipos de stub e tipos de Shim para personalizar dinamicamente o comportamento de membros individuais de stub. Para obter mais informações, consulte [isolando código em teste com falsificações da Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md).

## <a name="related-articles"></a>Artigos relacionados

|Title|Descrição|
|-----------|-----------------|
|[IntelliTrace](../debugger/intellitrace.md)|Descreve como depurar soluções do Visual Studio com mais facilidade usando o IntelliTrace.|
|[Walkthrough: Depurar um aplicativo do SharePoint usando o IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|Demonstra como encontrar erros de codificação em um projeto do SharePoint usando o IntelliTrace.|
|[Teste de unidade de código](../test/unit-test-your-code.md)|Descreve como encontrar erros lógicos em seu código usando testes de unidade.|

## <a name="see-also"></a>Confira também

- [Melhorar a qualidade do código](../test/improve-code-quality.md)
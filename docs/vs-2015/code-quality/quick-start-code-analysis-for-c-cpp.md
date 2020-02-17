---
title: 'Início Rápido: análise de código para CC++ -| Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
ms.assetid: 6110b8ba-0af6-4acd-b1ba-bb0551f90e44
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: e9db06ec0748ce4499afb423fac03886cd763301
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77278485"
---
# <a name="quick-start-code-analysis-for-cc"></a>Início Rápido: análise de código para C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode melhorar a qualidade do seu aplicativo executando a análise de código regularmente em C C++ ou Code. Isso pode ajudá-lo a encontrar problemas comuns, violações de boa prática de programação ou defeitos que são difíceis de descobrir por meio de testes. Os avisos da análise de código diferem dos erros e avisos do compilador porque a análise de código procura por padrões de código específicos que são válidos, mas que ainda podem criar problemas para você ou outras pessoas que usam seu código.  
  
## <a name="in-this-topic"></a>Neste tópico  
  
- [Configurar conjuntos de regras para um projeto](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_ConfigureRuleSets)  
  
- [Executar análise de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Run)  
  
- [Analisar e resolver avisos de análise de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Analyze)  
  
- [Suprimindo avisos da análise de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Suppress)  
  
- [Criando itens de trabalho para avisos de análise de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Creating_work_items_for_code_analysis_warnings)  
  
- [Pesquisando e filtrando resultados de análise de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Search)  
  
## <a name="BKMK_ConfigureRuleSets"></a>Configurar conjuntos de regras para um projeto  
  
1. Em **Gerenciador de soluções**, abra o menu de atalho para o nome do projeto e escolha **Propriedades**.  
  
2. As etapas a seguir são opcionais:  
  
    1. Nas listas de **configuração** e **plataforma** , escolha a configuração de compilação e a plataforma de destino.  
  
    2. Por padrão, a análise de código não relate os avisos de código que é gerado automaticamente por ferramentas externas. Para exibir avisos do código gerado, desmarque a caixa de seleção **suprimir resultados do código gerado** .  
  
        > [!NOTE]
        > Essa opção não suprime erros de análise de código e avisos do código gerado quando os erros e avisos que aparecem em formulários e modelos. Você pode exibir e manter o código-fonte de um formulário ou de um modelo.  
  
3. Para executar a análise de código toda vez que o projeto for criado usando a configuração selecionada, marque a caixa de seleção **Habilitar análise de código para CC++ /no Build** . Você também pode executar a análise de código manualmente abrindo o menu **analisar** e, em seguida, escolhendo **executar análise de código no** *ProjectName*.  
  
4. Na lista **executar este conjunto de regras** , siga um destes procedimentos:  
  
    - Escolha o conjunto de regras que você deseja usar.  
  
    - Escolha **\<procurar... >** especificar um conjunto de regras personalizadas existente que não esteja na lista.  
  
    - Defina um conjunto de regras personalizadas.  
  
         Para obter mais informações, consulte [criando conjuntos de regras personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
### <a name="standard-cc-rule-sets"></a>Conjuntos de regrasC++ /C padrão  
 O Visual Studio inclui dois conjuntos padrão de regras para código nativo:  
  
|Conjunto de regras|DESCRIÇÃO|  
|--------------|-----------------|  
|Regras recomendadas mínimas do Microsoft Native|Esse conjunto de regras enfoca os problemas mais críticos em seu código nativo, incluindo falhas potenciais de segurança e falhas do aplicativo. Você deve incluir esse conjunto de regras em qualquer conjunto personalizado de regras que você criar para seus projetos nativos.|  
|Regras nativas recomendadas da Microsoft|Esse conjunto de regras aborda uma ampla gama de problemas. Ele inclui todas as regras nas regras recomendadas do mínimo nativo da Microsoft.|  
  
## <a name="BKMK_Run"></a>Executar análise de código  
 Na página análise de código das páginas de propriedades do projeto, você pode configurar a análise de código para ser executada cada vez que criar seu projeto. Você também pode executar a análise de código manualmente.  
  
 Para executar a análise de código em uma solução:  
  
- No menu **Compilar**, escolha **Executar Análise de Código na Solução**.  
  
  Para executar a análise de código em um projeto:  
  
- Em Gerenciador de Soluções, escolha o nome do projeto.  
  
- No menu **Compilar** , escolha **executar análise de código no** *nome do projeto*.  
  
  O projeto ou solução é compilado e a análise de código é executada. Os resultados aparecem na janela Análise de Código.  
  
## <a name="BKMK_Analyze"></a>Analisar e resolver avisos de análise de código  
 Para analisar um aviso específico, escolha o título do aviso na janela Análise de Código. O aviso se expande para exibir informações adicionais sobre o problema. Quando possível, a análise de código exibe os números de linha e a lógica de análise que levaram ao aviso. Para obter informações detalhadas sobre o aviso, incluindo possíveis soluções para o problema, escolha a ID de aviso para exibir o tópico da ajuda na biblioteca MSND da mensagem.  
  
 {1&gt;Quando você expande um aviso, a linha de código que o causou é realçada no editor de códigos do Visual Studio.&lt;1}  
  
 Depois de entender o problema, você pode resolvê-lo no seu código. Em seguida, torne a executar a análise de código para verificar se o aviso não aparece mais na janela Análise de Código e se a sua correção não gerou novos avisos.  
  
> [!TIP]
> Você pode executar a análise de código novamente na janela Análise de Código. Escolha o botão **analisar** e escolha o escopo da análise. A análise pode ser executada na solução inteira ou em um projeto selecionado.  
  
## <a name="BKMK_Suppress"></a> Suprimindo avisos da análise de código  
 Há ocasiões em que você pode decidir não corrigir um aviso de análise de código. Você pode decidir que resolver o aviso exige recodificação demais considerando a probabilidade de que o problema ocorrerá em qualquer implementação do seu código no mundo real. Ou você pode achar que a análise usada no aviso é inadequada nesse contexto específico. É possível suprimir avisos individuais para que não apareçam mais na janela Análise de Código.  
  
 Para suprimir um aviso:  
  
1. Se as informações detalhadas não forem exibidas, escolha o título do aviso para expandi-la.  
  
2. Escolha o link **Ações** na parte inferior do aviso.  
  
3. Escolha **suprimir mensagem** e, em seguida, escolha **na fonte**.  
  
   Suprimir uma mensagem insere `#pragma warning (disable:`*WarningId*`)`, que suprime o aviso para a linha de código.  
  
## <a name="BKMK_Creating_work_items_for_code_analysis_warnings"></a>Criando itens de trabalho para avisos de análise de código  
 Você pode usar o recurso de acompanhamento de item de trabalho para registrar bugs de dentro do Visual Studio. Para usar esse recurso, você deve se conectar a uma instância do Team Foundation Server.  
  
 **Para criar um item de trabalho para um ou mais avisosC++ C/Code**  
  
1. Na janela análise de código, expanda e selecione os avisos  
  
2. No menu de atalho para os avisos, escolha **Criar item de trabalho**e, em seguida, escolha o tipo de item de trabalho.  
  
3. O Visual Studio cria um único item de trabalho para os avisos selecionados e exibe o item de trabalho em uma janela de documento do IDE.  
  
4. Adicione informações adicionais e, em seguida, escolha **salvar item de trabalho**.  
  
## <a name="BKMK_Search"></a> Pesquisando e filtrando resultados de análise de código  
 {1&gt;Você pode pesquisar listas longas de mensagens de aviso e filtrar avisos em soluções multiprojeto.&lt;1}  
  
1. **Para filtrar avisos por ID de aviso ou título**: Insira a palavra-chave na caixa de texto de **filtro** .  
  
2. **Para filtrar avisos por projeto**: em uma solução de vários projetos, escolha um ou mais projetos na lista no canto superior direito da janela de análise de código. Escolha o nome da solução para exibir todos os avisos.  
  
3. **Para filtrar avisos por severidade**: por padrão, as mensagens de análise de código recebem uma severidade de **aviso**. Você pode atribuir a severidade de uma ou mais mensagens como **erro** em um conjunto de regras personalizadas. Escolha **aviso** ou **erro** para exibir apenas as mensagens que recebem a respectiva severidade. Escolha **todos** para exibir todas as mensagens.

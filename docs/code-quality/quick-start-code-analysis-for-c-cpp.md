---
title: 'Início Rápido: Análise de código para C/C++'
description: Execute a análise estática C++ no código do Visual Studio para detectar problemas comuns de codificação e defeitos.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: b14737c09cf7ff2b14eda1f61408b531b9c22c14
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018373"
---
# <a name="quickstart-code-analysis-for-cc"></a>Início Rápido: Análise de código para C/C++

Você pode melhorar a qualidade do seu aplicativo executando a análise de código regularmente em C C++ ou Code. Isso pode ajudá-lo a encontrar problemas comuns, violações de boa prática de programação ou defeitos que são difíceis de descobrir por meio de testes. Os avisos da análise de código diferem dos erros e avisos do compilador porque a análise de código procura por padrões de código específicos que são válidos, mas que ainda podem criar problemas para você ou outras pessoas que usam seu código.

## <a name="configure-rule-sets-for-a-project"></a>Configurar conjuntos de regras para um projeto

1. Em **Gerenciador de soluções**, abra o menu de atalho para o nome do projeto e escolha **Propriedades**.

2. As etapas a seguir são opcionais:

    1. Nas listas de **configuração** e **plataforma** , escolha a configuração de compilação e a plataforma de destino.

    2. Por padrão, a análise de código não relate os avisos de código que é gerado automaticamente por ferramentas externas. Para exibir avisos do código gerado, desmarque a **Suprimir resultados do código gerado** caixa de seleção.

        > [!NOTE]
        > Essa opção não suprime erros de análise de código e avisos do código gerado quando os erros e avisos que aparecem em formulários e modelos. Você pode exibir e manter o código-fonte de um formulário ou de um modelo.

3. Para executar a análise de código toda vez que o projeto for criado usando a configuração selecionada, marque a caixa de seleção **Habilitar análise de código para CC++ /no Build** . Você também pode executar a análise de código manualmente abrindo o menu **analisar** e, em seguida, escolhendo **executar análise de código no** *ProjectName*.

4. No **executar este conjunto de regras** lista, siga um destes procedimentos:

    - Escolha o conjunto de regras que você deseja usar.

    - Escolha **\<Browse >** para especificar um conjunto de regras personalizadas existente que não esteja na lista.

    - Definir um [conjunto de regras personalizado](../code-quality/how-to-create-a-custom-rule-set.md).

### <a name="standard-cc-rule-sets"></a>Conjuntos de regrasC++ /C padrão

O Visual Studio inclui dois conjuntos padrão de regras para código nativo:

|Conjunto de regras|Descrição|
|--------------|-----------------|
|Regras recomendadas mínimas do Microsoft Native|Esse conjunto de regras enfoca os problemas mais críticos em seu código nativo, incluindo falhas potenciais de segurança e falhas do aplicativo. Você deve incluir esse conjunto de regras em qualquer conjunto personalizado de regras que você criar para seus projetos nativos.|
|Regras nativas recomendadas da Microsoft|Esse conjunto de regras aborda uma ampla gama de problemas. Ele inclui todas as regras nas regras recomendadas do mínimo nativo da Microsoft.|

## <a name="run-code-analysis"></a>Executar análise de código

Na página análise de código das páginas de propriedades do projeto, você pode configurar a análise de código para ser executada cada vez que criar seu projeto. Você também pode executar a análise de código manualmente.

Para executar a análise de código em uma solução:

- No menu **Compilar**, escolha **Executar Análise de Código na Solução**.

Para executar a análise de código em um projeto:

1. Em Gerenciador de Soluções, escolha o nome do projeto.

2. No menu **Compilar** , escolha **executar análise de código no** *nome do projeto*.

   O projeto ou solução é compilado e a análise de código é executada. Os resultados aparecem na Lista de Erros.

## <a name="analyze-and-resolve-code-analysis-warnings"></a>Analisar e resolver avisos de análise de código

Para analisar um aviso específico, escolha o título do aviso no Lista de Erros. O aviso se expande para exibir informações adicionais sobre o problema. Quando possível, a análise de código exibe os números de linha e a lógica de análise que levaram ao aviso. Para obter informações detalhadas sobre o aviso, incluindo possíveis soluções para o problema, escolha a ID de aviso para exibir seu tópico de ajuda online correspondente.

Quando você seleciona um aviso, a linha de código que causou o aviso é realçada no editor de código do Visual Studio.

Depois de entender o problema, você pode resolvê-lo no seu código. Em seguida, execute novamente a análise de código para certificar-se de que o aviso não aparecerá mais na Lista de Erros e que sua correção não gerou nenhum aviso novo.

## <a name="suppress-code-analysis-warnings"></a>Suprimir avisos de análise de código

Há ocasiões em que você pode decidir não corrigir um aviso de análise de código. Você pode decidir que resolver o aviso exige recodificação demais considerando a probabilidade de que o problema ocorrerá em qualquer implementação do seu código no mundo real. Ou você pode achar que a análise usada no aviso é inadequada nesse contexto específico. Você pode suprimir avisos individuais para que eles não apareçam mais no Lista de Erros.

Para suprimir um aviso:

1. Se as informações detalhadas não forem exibidas, escolha o título do aviso para expandi-la.

2. Escolha o link **Ações** na parte inferior do aviso.

3. Escolha **suprimir mensagem** e, em seguida, escolha **na fonte**.

   Suprimir uma mensagem insere `#pragma warning (disable:[warning ID])` que suprime o aviso para a linha de código.

## <a name="create-work-items-for-code-analysis-warnings"></a>Criar itens de trabalho para avisos de análise de código

Você pode usar o recurso de acompanhamento de item de trabalho para registrar bugs de dentro do Visual Studio. Para usar esse recurso, você deve se conectar a uma instância do Team Foundation Server.

**Para criar um item de trabalho para um ou mais avisosC++ C/Code**

1. Na Lista de Erros, expanda e selecione os avisos

2. No menu de atalho para os avisos, escolha **Criar item de trabalho**e, em seguida, escolha o tipo de item de trabalho.

3. O Visual Studio cria um único item de trabalho para os avisos selecionados e exibe o item de trabalho em uma janela de documento do IDE.

4. Adicione informações adicionais e, em seguida, escolha **salvar item de trabalho**.

## <a name="search-and-filter-code-analysis-results"></a>Pesquisar e filtrar resultados da análise de código

Você pode pesquisar listas longas de mensagens de aviso e pode filtrar avisos em soluções multiprojeto.

- **Para filtrar avisos por ID de aviso ou título**: Insira a palavra-chave na caixa de pesquisa.

- **Para filtrar avisos por severidade**: Por padrão, as mensagens de análise de código recebem uma severidade de **aviso**. Você pode atribuir a severidade de uma ou mais mensagens como **erro** em um conjunto de regras personalizadas. Na coluna **severidade** da **lista de erros**, escolha a seta suspensa e, em seguida, o ícone de filtro. Escolha **aviso** ou **erro** para exibir apenas as mensagens que recebem a respectiva severidade. Escolha **selecionar tudo** para exibir todas as mensagens.

## <a name="see-also"></a>Consulte também

[Análise de código para C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
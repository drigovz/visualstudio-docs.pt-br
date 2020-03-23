---
title: Configure o escopo de análise de código ao vivo para código gerenciado
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 300e3f276a45cfe2115311c7d27eedce365616cf
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432234"
---
# <a name="how-to-configure-live-code-analysis-scope-for-managed-code"></a>Como: Configurar o escopo de análise de código ao vivo para código gerenciado

## <a name="what-is-live-code-analysis-for-managed-code"></a>O que é "Análise de código ao vivo" para código gerenciado?
O Visual Studio executa um monte de análises de código ao vivo, também referidas como *análise de fundo,* enquanto você está editando arquivos de origem no editor. Algumas delas são necessárias análises mínimas para uma experiência de edição aceitável do Visual Studio IDE. Parte disso é para uma melhor capacidade de resposta para os recursos do IDE. Enquanto parte disso é para habilitar funcionalidades adicionais de IDE, como diagnósticos e correções de código de analisadores Roslyn. Com base na funcionalidade, essas análises podem ser agrupadas da seguinte forma:

- **Cálculo de fundo de diagnósticos**: Análise para calcular erros, avisos e sugestões em arquivos de origem. Esses diagnósticos aparecem como entradas na lista de erros e como rabiscos no editor. Eles podem ser classificados em duas categorias:
    - Diagnósticos do compilador C# e Visual Basic
    - Diagnósticos do analisador roslyn, que inclui:

        - Analisadores IDE incorporados para sugestões de estilo de código e
        - Pacotes de analisadores de terceiros [instalados](./install-roslyn-analyzers.md) para projetos na solução atual.

- **Outras análises de fundo**: Análise para melhorar a capacidade de resposta e interação visual do Estúdio Visual para recursos iDE. Alguns exemplos de tais análises são:
    - Análise de antecedentes de arquivos abertos.
    - Compilação de fundos de projetos com arquivos abertos para realizar símbolos para melhor capacidade de resposta de certos recursos do IDE.
    - Construindo sintaxe e caches de símbolos.
    - Detectando associação de designers para arquivos de origem, como formulários, controles, etc.

## <a name="default-analysis-scope"></a>Escopo de análise padrão

Por padrão, a análise de código ao vivo para computação em segundo plano de diagnósticos é executada para todos os arquivos que são _abertos_ no Visual Studio. Poucas das _outras análises de fundo mencionadas_ acima executam para todos os projetos, que têm pelo menos um arquivo aberto. Enquanto poucas análises de fundo executam toda a solução.

## <a name="custom-analysis-scope"></a>Escopo de análise personalizado

O escopo padrão de cada análise de fundo foi ajustado para a experiência, funcionalidade e desempenho ideais do usuário para a maioria dos cenários e soluções do cliente. No entanto, há casos em que os clientes podem querer personalizar esse escopo para diminuir ou aumentar a análise de fundo. Por exemplo: 

- Modo de economia de energia: Se os usuários estiverem executando a bateria do laptop, eles podem querer minimizar o consumo de energia por uma maior duração da bateria. Nesse cenário, eles gostariam de minimizar a análise de fundo.
- Análise de código demanda: Se os usuários preferem desativar a execução do analisador ao vivo e executar manualmente a análise de código demanda, eles gostariam de minimizar a análise de fundo. [Veja Como: Executar manualmente a análise de código demanda](./how-to-run-code-analysis-manually-for-managed-code.md).
- Análise completa da solução: Se os usuários quiserem ver sempre todos os diagnósticos em todos os arquivos da solução, independentemente de estarem abertos no editor ou não. Nesse cenário, eles gostariam de maximizar o escopo de análise de fundo para toda a solução.

A partir da versão 16.5 do Visual Studio 2019, os usuários podem personalizar explicitamente o escopo de todas as análises de código ao vivo, incluindo computação de diagnóstico, para projetos C# e Visual Basic. Os escopos de análise disponíveis são:

- **Documento atual**: Minimiza o escopo de análise de código ao vivo para executar apenas para o arquivo atual ou visível no editor.
- **Documentos abertos**: Escopo padrão de análise de código vivo, conforme descrito na seção acima.
- **Solução inteira**: Maximiza o escopo de análise de código ao vivo para executar todos os arquivos e projetos em toda a solução.

Você pode escolher um dos escopos de análise personalizados acima no diálogo Opções de ferramentas seguindo as etapas abaixo:

1. Para abrir a caixa de diálogo **Opções,** na barra de menus no Visual Studio escolha **Opções de** > **ferramentas**.

2. Na caixa de diálogo **Opções,** escolha **Editor de** > texto**C#** ou **Avançado Básico** > **.**

3. Selecione o **escopo de análise de fundo** desejado para personalizar o escopo de análise. Escolha **OK** quando terminar.

![Escopo de análise.](./media/background-analysis-scope.png)

> [!NOTE]
> Antes do Visual Studio 2019 versão 16.5, os usuários podem personalizar o escopo de análise para computação de diagnóstico para toda a solução usando a caixa **de seleção de análise de solução completa** do **Tools** > **Options** > Text**Editor** > **C#** ou da guia **Basic** > **Advanced.** Não há suporte para minimizar o escopo de análise de fundo em versões anteriores do Visual Studio.

## <a name="automatically-minimize-live-code-analysis-scope"></a>Minimizar automaticamente o escopo de análise de código ao vivo

Se o Visual Studio detectar que 200 MB ou menos de memória do sistema está disponível para ele, ele minimizará automaticamente o escopo de análise de código ao vivo para "Documento Atual". Se isso ocorrer, um alerta aparecerá informando que o Visual Studio desativou alguns recursos. Um botão permite que você volte ao escopo de análise anterior, se quiser.

![Texto de alerta minimizando o escopo da análise](./media/fsa_alert.png)

## <a name="see-also"></a>Confira também

- [Suspensão automática de recursos](./automatic-feature-suspension.md)
- [Solicitação de recurso de modo de economia de energia](https://github.com/dotnet/roslyn/issues/38429)

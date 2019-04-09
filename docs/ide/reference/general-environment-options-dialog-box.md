---
title: Caixa de diálogo Geral, Ambientes, Opções
ms.date: 03/28/2019
ms.topic: reference
f1_keywords:
- VS.Message.0x800a002e
- VS.ToolsOptionsPages.Environment.General
- VS.Environment.General
helpviewer_keywords:
- MRU lists
- windows, customizing
- MDI, environment options
- speed, environment animation
- File menu
- menus, customizing
- Windows menu customizing
- status bars, displaying
- IDE, startup options
- editors, autocompletion
- Options dialog box, General Environment
- General Environment Options dialog box
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fdbd8c64514854aa77c358145badbf6583996f1
ms.sourcegitcommit: b14b7a938a2aba9fcce4d5e813aadf2040b0dcda
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58647265"
---
# <a name="options-dialog-box-environment--general"></a>Caixa de diálogo Opções: Ambiente \> Geral

Use esta página para alterar temas de cores, configurações de barra de status e associações de extensões de arquivo, entre outras coisas, para o IDE (ambiente de desenvolvimento integrado). Você pode acessar a caixa de diálogo **Opções** abrindo o menu **Ferramentas**, escolhendo **Opções**, abrindo a pasta **Ambiente** e, em seguida, escolhendo a página **Geral**. Se essa página não aparecer na lista, marque a caixa de seleção **Mostrar todas as configurações** na caixa de diálogo **Opções**.

## <a name="visual-experience"></a>Experiência visual

**Tema de cores**

Escolha o tema de cor **Azul**, **Claro**, **Escuro** ou **Azul (contraste extra)** para o IDE.

É possível instalar temas predefinidos adicionais e criar temas personalizados, baixando e instalando o **Visual Studio Color Theme Editor** do [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Após instalar essa ferramenta, temas de cores adicionais aparecerão na caixa de listagem **Tema de Cor**.

**Aplicar o estilo de capitalização de título à barra de menus**

Os menus utilizam o estilo de capitalização de título como padrão. Desmarque essa opção para usar o estilo de capitalização em todas as letras.

::: moniker range=">=vs-2019"

**Otimizar a renderização de telas com diferentes densidades de pixel (requer reinicialização)**

Esta opção habilita ou desabilita o reconhecimento de DPI (pontos por polegada) por monitor (ou *PMA*). Quando o PMA está habilitado, a interface de usuário do Visual Studio é exibida com nitidez em qualquer fator de escala de exibição do monitor e configuração de DPI, inclusive com a extensão a vários monitores. Para habilitar o PMA, é necessária a atualização do Windows 10 de 10 de abril de 2018 ou posterior e o .NET Framework 4.8 ou posterior. Essa opção aparecerá desativada se esses dois pré-requisitos não forem atendidos.

::: moniker-end

**Ajustar autom. a experiência visual com base no desempenho do cliente**

Especifica se o Visual Studio ajusta automaticamente a experiência visual ou se você a ajusta de maneira explícita. Esse ajuste pode alterar a exibição de cores de gradientes para cores simples ou pode restringir o uso de animações em menus ou janelas pop-up.

**Habilitar experiência avançada do cliente**

Habilita a experiência visual completa do Visual Studio, incluindo animações e gradientes. Desmarque esta opção quando estiver usando conexões da Área de Trabalho Remota ou adaptadores de gráficos mais antigos, uma vez que esses recursos podem ter um desempenho ruim nesses casos. Essa opção fica disponível somente quando você desmarca a opção **Ajustar autom. a experiência visual com base no desempenho do cliente**.

**Usar aceleração de elementos gráficos de hardware se disponível**

Usa aceleração de elementos gráficos de hardware se estiver disponível, em vez de aceleração de software.

## <a name="other"></a>Outros

**Itens a serem mostrados no menu Janela**

Personaliza o número de janelas que aparecem na lista Janelas do menu **Janela**. Insira um número entre 1 e 24. O valor padrão é 10.

**Itens mostrados em listas usadas recentemente**

Personaliza o número de projetos e arquivos usados mais recentemente que aparecem no menu **Arquivo**. Insira um número entre 1 e 24. O valor padrão é 10. Esta é uma maneira fácil de recuperar projetos e arquivos usados recentemente.

**Mostrar barra de status**

Exibe a barra de status. A barra de status fica localizada na parte inferior da janela do IDE e exibe informações sobre o progresso das operações em andamento.

**Botão Fechar afeta apenas a janela da ferramenta ativa**

Especifica que, quando o botão **Fechar** é acionado, somente a janela da ferramenta que está em foco é fechada, e não todas as janelas de ferramentas do conjunto encaixado. Por padrão, essa opção é selecionada.

**Botão Ocultar Automaticamente afeta apenas a janela da ferramenta ativa**

Especifica que, quando o botão **Ocultar Automaticamente** é acionado, somente a janela da ferramenta que está em foco é ocultada automaticamente, e não todas as janelas de ferramentas do conjunto encaixado. Por padrão, essa opção não é selecionada.

## <a name="see-also"></a>Consulte também

- [Caixa de diálogo Opções do Ambiente](../../ide/reference/environment-options-dialog-box.md)
- [Personalizando layouts de janela](../../ide/customizing-window-layouts-in-visual-studio.md)
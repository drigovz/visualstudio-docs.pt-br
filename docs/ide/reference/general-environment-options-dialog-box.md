---
title: Caixa de diálogo Geral, Ambientes, Opções
description: Saiba como usar a página Geral na seção ambiente para alterar temas de cor, configurações de barra de status, associações de extensão de arquivo e muito mais para o IDE.
ms.custom: SEO-VS-2020
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- VS.Environment.General
- VS.Message.0x800a002e
- VS.OptionsDialog.Environment
- VS.ToolsOptionsPages.Environment
- VS.ToolsOptionsPages.Environment.General
helpviewer_keywords:
- recently used file lists
- Windows menu, customizing
- status bar, displaying
- Options dialog box, General Environment
- General Environment Options dialog box
- Environment Options dialog box
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b58cf19406d49c175a07ab5e3dad60fd0354c656
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969692"
---
# <a name="options-dialog-box-environment--general"></a>Caixa de diálogo opções: ambiente \> geral

Use esta página para alterar temas de cores, configurações de barra de status e associações de extensões de arquivo, entre outras coisas, para o IDE (ambiente de desenvolvimento integrado). Você pode acessar a caixa de diálogo **Opções** abrindo o menu **Ferramentas**, escolhendo **Opções**, abrindo a pasta **Ambiente** e, em seguida, escolhendo a página **Geral**.

## <a name="visual-experience"></a>Experiência visual

**Tema de cores**

Escolha o tema de cor **Azul**, **Claro**, **Escuro** ou **Azul (contraste extra)** para o IDE.

É possível instalar temas predefinidos adicionais e criar temas personalizados, baixando e instalando o **Visual Studio Color Theme Editor** do [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Após instalar essa ferramenta, temas de cores adicionais aparecerão na caixa de listagem **Tema de Cor**.

**Aplicar o estilo de capitalização de título à barra de menus**

Os menus utilizam o estilo de capitalização de título como padrão. Desmarque essa opção para usar o estilo de capitalização em todas as letras.

::: moniker range=">=vs-2019"

**Otimizar a renderização de telas com diferentes densidades de pixel (requer reinicialização)**

Esta opção habilita ou desabilita o reconhecimento de DPI (pontos por polegada) por monitor (ou *PMA*). Quando o PMA está habilitado, a interface de usuário do Visual Studio é exibida com nitidez em qualquer fator de escala de exibição do monitor e configuração de DPI, inclusive com a extensão a vários monitores. Para habilitar o PMA, é necessária a atualização do Windows 10 de 10 de abril de 2018 ou posterior e o .NET Framework 4.8 ou posterior. Essa opção aparecerá desativada se esses dois pré-requisitos não forem atendidos.

> [!TIP]
> - O Windows 10 tem uma configuração que diz **Permitir que o Windows tente corrigir aplicativos para que eles não fiquem desfocados**. **Ativar** essa configuração do Windows terá um efeito insignificante se a opção **Otimizar renderização para telas com densidades de pixel diferentes** estiver marcada.
> - O Windows 10 também inclui uma **Solução de problemas de compatibilidade de programas**. Não é recomendável tentar corrigir a aparência do Visual Studio usando essa solução de problemas.

::: moniker-end

**Ajustar automaticamente a experiência visual com base no desempenho do cliente**

Especifica se o Visual Studio ajusta automaticamente a experiência visual ou se você a ajusta de maneira explícita. Esse ajuste pode alterar a exibição de cores de gradientes para cores simples ou pode restringir o uso de animações em menus ou janelas pop-up.

::: moniker range="vs-2017"

> [!TIP]
> O Windows 10 tem uma configuração que diz **Permitir que o Windows tente corrigir aplicativos para que eles não fiquem desfocados**. É recomendável **ativar** essa configuração se o Visual Studio ficar desfocado no monitor. Considere atualizar para o [Visual Studio 2019](https://visualstudio.microsoft.com/downloads), que melhorou significativamente a nitidez de exibição por ser um aplicativo com suporte a pontos por polegada por monitor.

::: moniker-end

**Habilitar experiência avançada do cliente**

Habilita a experiência visual completa do Visual Studio, incluindo animações e gradientes. Desmarque esta opção quando estiver usando conexões da Área de Trabalho Remota ou adaptadores de gráficos mais antigos, uma vez que esses recursos podem ter um desempenho ruim nesses casos. Essa opção fica disponível somente quando você desmarca a opção **Ajustar autom. a experiência visual com base no desempenho do cliente**.

**Usar aceleração de elementos gráficos de hardware, se disponível**

Usa aceleração de elementos gráficos de hardware se estiver disponível, em vez de aceleração de software.

## <a name="other"></a>Outro

**Itens a serem mostrados no menu Janela**

Personaliza o número de janelas que aparecem na lista Janelas do menu **Janela**. Insira um número entre 1 e 24. O valor padrão é 10.

**Itens mostrados em listas usadas recentemente**

Personaliza o número de projetos e arquivos usados mais recentemente que aparecem no menu **Arquivo**. Insira um número entre 1 e 24. O valor padrão é 10. Esta é uma maneira fácil de recuperar projetos e arquivos usados recentemente.

**Mostrar barra de status**

Exibe a barra de status. A barra de status fica localizada na parte inferior da janela do IDE e exibe informações sobre o progresso das operações em andamento.

**O botão Fechar afeta apenas a janela da ferramenta ativa**

Especifica que, quando o botão **Fechar** é acionado, somente a janela da ferramenta que está em foco é fechada, e não todas as janelas de ferramentas do conjunto encaixado. Por padrão, essa opção é selecionada.

**O botão Ocultar Automaticamente afeta apenas a janela da ferramenta ativa**

Especifica que, quando o botão **Ocultar Automaticamente** é acionado, somente a janela da ferramenta que está em foco é ocultada automaticamente, e não todas as janelas de ferramentas do conjunto encaixado. Por padrão, essa opção não é selecionada.

## <a name="see-also"></a>Confira também

- [Personalizar layouts de janela](../../ide/customizing-window-layouts-in-visual-studio.md)

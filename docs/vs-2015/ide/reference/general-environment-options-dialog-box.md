---
title: Caixa de diálogo Geral, Ambiente, Opções | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
- Visual Studio Start page, setting
- IDE, startup options
- editors, autocompletion
- Options dialog box, General Environment
- General Environment Options dialog box
ms.assetid: 90fc2e6f-572f-4384-96d8-5678299ce58e
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 83fc6adeba0529be03a9a982713d0584a2a7bc45
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661271"
---
# <a name="general-environment-options-dialog-box"></a>Caixa de diálogo Geral, Ambientes, Opções
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use esta página para alterar temas de cores, configurações de barra de status e associações de extensões de arquivo, entre outras coisas, para o IDE (ambiente de desenvolvimento integrado). Você pode acessar a caixa de diálogo **Opções** abrindo o menu **Ferramentas**, escolhendo **Opções**, abrindo a pasta **Ambiente** e, em seguida, escolhendo a página **Geral**. Se essa página não aparecer na lista, marque a caixa de seleção **Mostrar todas as configurações** na caixa de diálogo **Opções**.

> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, abra o menu **Ferramentas** e escolha **Importar e Exportar Configurações**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="visual-experience"></a>Experiência visual
 **Tema de cores** Escolha o tema de cor **azul**, **claro** ou **escuro** para o IDE.

 Para instalar temas predefinidos adicionais e criar temas personalizados, baixe e instale o **Visual Studio 2015 Color Theme Editor** do [Visual Studio Marketplace](https://marketplace.visualstudio.com). Após você instalar essa ferramenta, temas de cores adicionais aparecem na caixa de listagem Tema da cor.

 A aplicação de maiúsculas e minúsculas nos menus da barra de menus estão em **maiúsculas e minúsculas** por padrão no Visual Studio 2015. Desmarque essa opção para defini-los como **TODAS EM MAIÚSCULAS**.

 **Ajustar automaticamente a experiência visual com base no desempenho do cliente** Especifica se o Visual Studio define o ajuste para a experiência visual automaticamente ou você define o ajuste explicitamente. Esse ajuste pode alterar a exibição de cores de gradientes para cores simples ou pode restringir o uso de animações em menus ou janelas pop-up.

 **Habilitar a experiência do cliente avançada** Habilita a experiência visual completa do Visual Studio, incluindo gradientes e animações. Desmarque esta opção quando estiver usando conexões da Área de Trabalho Remota ou adaptadores de gráficos mais antigos, uma vez que esses recursos podem ter um desempenho ruim nesses casos. Essa opção fica disponível somente quando você desmarca a opção **Ajustar autom. a experiência visual com base no desempenho do cliente**.

 **Usar aceleração de gráficos de hardware, se disponível** Usa a aceleração de gráficos de hardware se ela estiver disponível, em vez de aceleração de software.

## <a name="other"></a>Outros
 **Itens mostrados no menu Janela** Personaliza o número de janelas que aparecem na lista Janelas do menu **Janela**. Digite um número entre 1 e 24. Por padrão, o número é 10.

 **Itens mostrados em listas usadas recentemente** Personaliza o número de projetos e arquivos usados mais recentemente que aparecem no menu **Arquivo**. Digite um número entre 1 e 24. Por padrão, o número é 10. Esta é uma maneira fácil de recuperar projetos e arquivos usados recentemente.

 **Mostrar barra de status** Exibe a barra de status. A barra de status fica localizada na parte inferior da janela do IDE e exibe informações sobre o progresso das operações em andamento.

 **Botão Fechar afeta apenas a janela de ferramentas ativa** Especifica que, quando o botão **Fechar** é acionado, somente a janela de ferramentas que está em foco é fechada e não todas as janelas de ferramentas do conjunto encaixado. Por padrão, essa opção é selecionada.

 **Botão Ocultar Automaticamente afeta apenas a janela de ferramentas ativa** Especifica que, quando o botão **Ocultar Automaticamente** é acionado, somente a janela de ferramentas que está em foco é ocultada automaticamente e não todas as janelas de ferramentas do conjunto encaixado. Por padrão, essa opção não é selecionada.

 **Gerenciar associações de arquivos** Exibe a caixa de diálogo **definir associações de programa do Windows** , em que é possível exibir extensões de arquivo para itens que normalmente são associados ao Visual Studio e ao programa padrão atual para abrir cada tipo de arquivo. Para fazer do Visual Studio o aplicativo padrão para os tipos de arquivos que ainda não estão associados a ele, escolha a extensão de arquivo e escolha **Salvar**.

 Essa opção pode ser útil se você tiver duas versões do Visual Studio instaladas no mesmo computador e, posteriormente, desinstalar uma das versões. Após a desinstalação, os ícones dos arquivos do Visual Studio não aparecem mais no Explorador de Arquivos. Além disso, o Windows deixa de reconhecer o Visual Studio como o aplicativo padrão para editar esses arquivos. Essa opção restaura as associações.

## <a name="see-also"></a>Consulte também
 [Caixa de diálogo opções de ambiente](../../ide/reference/environment-options-dialog-box.md) [Personalizando layouts de janela](../../ide/customizing-window-layouts-in-visual-studio.md)

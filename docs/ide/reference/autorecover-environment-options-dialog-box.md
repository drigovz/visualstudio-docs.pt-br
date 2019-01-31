---
title: AutoRecover, Caixa de diálogo Opções, Ambiente
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6b65da35a180e507af8175d7e1c8e209e84ba8d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993982"
---
# <a name="autorecover-environment-options-dialog-box"></a>Caixa de diálogo AutoRecuperação, Ambiente, Opções

Use essa página da caixa de diálogo **Opções** para especificar se o backup automático dos arquivos deve ser feito ou não. Especifique também se deseja restaurar os arquivos modificados caso o Visual Studio seja desligado inesperadamente.

Acesse essa caixa de diálogo selecionando o menu **Ferramentas**, escolhendo **Opções** e, em seguida, clicando em **Ambiente** > **AutoRecuperação**. Se essa página não aparecer na lista, selecione **Mostrar todas as configurações** na caixa de diálogo **Opções**.

**Salvar informações de AutoRecuperação a cada [n] minutos**

Use esta opção para personalizar a frequência com que um arquivo é salvo automaticamente no editor. Para arquivos já salvos, uma cópia do arquivo é salva em *%USERPROFILE%\Documents\Visual Studio\\[versão]\Backup Files\\[nomedoprojeto]*. Se o arquivo for novo e você ainda não o tiver salvado, ele será salvo automaticamente com um nome de arquivo gerado aleatoriamente.

**Manter informações de AutoRecuperação por [n] dias**

Use esta opção para especificar por quanto tempo o Visual Studio manterá arquivos criados para AutoRecuperação.

### <a name="see-also"></a>Consulte também

- [Caixa de diálogo de opções](../../ide/reference/options-dialog-box-visual-studio.md)
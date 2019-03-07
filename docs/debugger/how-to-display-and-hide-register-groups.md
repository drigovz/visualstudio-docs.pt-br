---
title: 'Como: Exibir e ocultar grupos de registro | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.registergroups
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, displaying and hiding register groups
- register groups, displaying and hiding
ms.assetid: 6be5dfb4-4cfe-4daf-b538-60405640857d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be702dcd19506e6da8fb1e291aa5262dbf4399b2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018443"
---
# <a name="how-to-display-and-hide-register-groups-c-c-visual-basic-f"></a>Como: Exibir e ocultar grupos de registro (C#, C++, Visual Basic, F#)

A janela **Registros** estará disponível apenas se a depuração do nível de endereços estiver habilitada na caixa de diálogo **Opções**, nó **Depuração**, categoria **Geral**.

Para reduzir a confusão, a janela **Registros** organiza os registros em grupos. Se você clicar com o botão direito do mouse na janela **Registros**, verá um menu de atalho contendo esses grupos, que você poderá exibir ou ocultar como achar melhor seguindo o procedimento abaixo.

> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Redefinir as configurações](../ide/environment-settings.md#reset-settings).

## <a name="display-or-hide-register-groups"></a>Exibir ou ocultar grupos de registros

1.  Clique com o botão direito do mouse na janela **Registros**.

2.  No menu de atalho, selecione os grupos de registro que você deseja mostrar ou ocultar.

     Os grupos de registro que não têm suporte pelo hardware no qual você está depurando estão desabilitados no menu de atalho, e não podem ser selecionados.

## <a name="see-also"></a>Consulte também

- [Como: Usar a janela Registros](../debugger/how-to-use-the-registers-window.md)
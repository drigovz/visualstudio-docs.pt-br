---
title: Caixa de diálogo Configurações Avançadas de Segurança | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
- vs.err.debug_in_zone_no_hostproc:11310
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 000c3c4e2996869e96fd0d6097b5bab8576936a7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651738"
---
# <a name="advanced-security-settings-dialog-box"></a>Caixa de diálogo Configurações de Segurança Avançadas
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Essa caixa de diálogo permite especificar configurações de segurança relacionadas à depuração na zona.

 Para acessar essa caixa de diálogo, selecione um nó do projeto no **Gerenciador de Soluções** e, no menu **Projeto**, clique em **Propriedades**. Quando o **Designer de Projeto** for exibido, clique na guia **Segurança**. Na página **Segurança** página, selecione **Habilitar Configurações de Segurança do ClickOnce**, clique em **Este é um aplicativo de confiança parcial** e, em seguida, clique em **Avançado**.

## <a name="uielement-list"></a>Lista UIElement
 **Depurar esse aplicativo com o conjunto de permissões selecionado** Se você marcar essa caixa de seleção, o conjunto de permissões selecionado na página **Segurança** será usado durante a depuração. Por padrão, essa opção é selecionada.

 Para depurar em uma zona de segurança para trabalhar, essa opção deve ser habilitada; além disso, a opção **Habilitar o processo de hospedagem do Visual Studio** (disponível na página **Depurar** página do **Designer de Projeto**) deve ser habilitada.

 Para projetos de Aplicativos de Navegador da Web WPF, a opção **Depurar este aplicativo com o conjunto de permissões selecionado** é marcada e desabilitada.

 **Conceder ao aplicativo acesso ao seu site de origem** Se você marcar esta caixa de seleção, o aplicativo poderá acessar o site ou o compartilhamento do servidor no qual ele está publicado. Por padrão, essa opção é selecionada.

 **Depurar esse aplicativo como se ele tivesse sido baixado da URL a seguir** Se você precisar permitir que o aplicativo acesse o site ou o compartilhamento de servidor correspondente à **URL de instalação** especificada na página **Publicar**, digite essa URL aqui. Essa opção está disponível apenas quando **Conceder ao aplicativo acesso ao site de origem** está selecionado.

## <a name="see-also"></a>Veja também
 [Página Segurança, Designer de Projeto](../../ide/reference/security-page-project-designer.md)

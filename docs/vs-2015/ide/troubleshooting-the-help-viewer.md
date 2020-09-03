---
title: Solução de problemas do Visualizador da Ajuda | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: troubleshooting
helpviewer_keywords:
- troubleshooting [Help Viewer 2.0]
- Help Viewer 2.0, troubleshooting
ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2cedc9f45d2e21684496bd882de4aa74b3bf8b3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851073"
---
# <a name="troubleshooting-the-help-viewer"></a>Solucionando problemas do Visualizador da Ajuda
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tópico aborda problemas que podem ocorrer com o Visualizador da Ajuda.

## <a name="audio-doesnt-work"></a>O áudio não funciona.
 O Visualizador da Ajuda não inclui um player de áudio. Se você baixar conteúdo que contém áudio e nada acontecer quando você escolher **Reproduzir**, instale um player de áudio.

## <a name="search-doesnt-work-in-windows-server-2008-windows-server-2008-with-sp1-or-windows-server-2008-r2"></a>A pesquisa não funciona no Windows Server 2008, no Windows Server 2008 com SP1 ou no Windows Server 2008 R2.
 Os recursos de pesquisa e filtro do Visualizador da Ajuda requerem que o serviço Windows Search esteja instalado. Por padrão, esse serviço fica desativado no Windows Server 2008, no Windows Server 2008 com Service Pack 1 (SP1) e no Windows Server 2008 R2.

#### <a name="to-activate-windows-search-service"></a>Para ativar o serviço Windows Search

1. Inicie o Gerenciador do Servidor.

2. No painel de navegação esquerdo, escolha **Funções**.

3. No painel Resumo de Funções, escolha **Adicionar Função**.

4. Escolha a função Serviços de Arquivo e escolha o botão **Avançar**.

5. Escolha o serviço de função do Windows Search.

## <a name="additional-resources"></a>Recursos adicionais
 Você pode obter mais informações e fornecer comentários sobre o Visualizador da Ajuda usando os seguintes recursos:

- Para fornecer comentários, consulte [Microsoft Connect](https://connect.microsoft.com/) no site da Microsoft ou enviar um email para [hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com).

- Para obter mais informações, consulte o fórum [Documentação do Desenvolvedor e Sistema de Ajuda](https://social.msdn.microsoft.com/Forums/en-US/devdocs/threads) e o blog [The Help Guy](https://blogs.msdn.com/b/thehelpguy/).

## <a name="see-also"></a>Consulte Também
 [Guia do administrador do Help Viewer 2.1](https://msdn.microsoft.com/library/hh492077(VS.110).aspx)

---
title: Interceptando comandos de serviço de linguagem legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5206bced8b4bfae32498434765e5c3f61801b386
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707445"
---
# <a name="intercepting-legacy-language-service-commands"></a>Interceptando comandos do serviço de linguagem herdado
Com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], você pode ter os comandos de interceptação de serviço de idioma que a exibição de texto lidaria de outra forma. Isso é útil para um comportamento específico do idioma que a exibição de texto não gerencia. Você pode interceptar esses comandos adicionando um ou mais filtros de comando à exibição de texto do seu serviço de idioma.

## <a name="getting-and-routing-the-command"></a>Obtenção e roteamento do Comando
 Um filtro de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> comando é um objeto que monitora certas seqüências de caracteres ou comandos-chave. Você pode associar mais de um filtro de comando a uma única exibição de texto. Cada visualização de texto mantém uma cadeia de filtros de comando. Depois de criar um novo filtro de comando, adicione o filtro à cadeia para a exibição de texto apropriada.

 Ligue <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para o método para adicionar seu filtro de comando à cadeia. Quando você <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ligar, retorna outro filtro de comando para o qual você pode passar os comandos que seu filtro de comando não manuseia.

 Você tem as seguintes opções para manipulação de comando:

- Manuseie o comando e passe o comando para o próximo filtro de comando na cadeia.

- Manuseie o comando e não passe o comando para o próximo filtro de comando.

- Não manuseie o comando, mas passe o comando para o próximo filtro de comando.

- Ignore o comando. Não manuseie-o no filtro de corrente e não passe-o para o próximo filtro.

  Para obter informações sobre quais comandos seu serviço de idioma deve lidar, consulte [Comandos importantes para filtros de serviço de idioma](../../extensibility/internals/important-commands-for-language-service-filters.md).

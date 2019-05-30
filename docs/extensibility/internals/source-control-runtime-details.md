---
title: Detalhes de tempo de execução do controle de origem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e84fd82c5da5deea2d718baf67799e5bf877131
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322555"
---
# <a name="source-control-runtime-details"></a>Detalhes de tempo de execução de controle do código-fonte
Um projeto é adicionado ao controle de origem quando o usuário adiciona um arquivo no projeto ao controle de origem, ou por meio de um controlador de automação, como um assistente. Um projeto não especifica para si mesmo que está sob controle do código-fonte; Ele dá suporte ao controle do código-fonte, mas deve ser adicionado manualmente a ele.

## <a name="registering-with-a-source-control-package"></a>Registrando com um pacote de controle do código-fonte
 Quando um arquivo em seu projeto é adicionado ao controle de origem, o ambiente chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> para fornecer a você quatro cadeias de caracteres opacas que são usadas como cookies pelo sistema de controle de origem. Store essas cadeias de caracteres no arquivo de projeto. Essas cadeias de caracteres devem ser passadas para o Stub de controle do código-fonte (o componente do Visual Studio que gerencia os pacotes de controle do código-fonte) durante a inicialização do tipo de projeto chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>. Isso por sua vez carrega o pacote de controle de origem apropriado e encaminha a chamada para sua implementação de `IVsSccManager2::RegisterSccProject`.

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Oferecer suporte ao controle do código-fonte](../../extensibility/internals/supporting-source-control.md)
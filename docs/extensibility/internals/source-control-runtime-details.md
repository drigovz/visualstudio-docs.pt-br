---
title: Detalhes do tempo de execução do controle de origem | Microsoft Docs
description: Saiba como um projeto é adicionado ao controle do código-fonte, seja quando um usuário adiciona um arquivo ao projeto no controle do código-fonte ou por meio de um controlador de automação.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 213b0096f2bea541fa55840f8f1ea78e8f195cd8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905759"
---
# <a name="source-control-runtime-details"></a>Detalhes de runtime de controle do código-fonte
Um projeto é adicionado ao controle do código-fonte quando o usuário adiciona um arquivo no projeto ao controle do código-fonte ou por meio de um controlador de automação, como um assistente. Um projeto não especifica se ele está sob controle do código-fonte; Ele dá suporte ao controle do código-fonte, mas deve ser adicionado a ele manualmente.

## <a name="registering-with-a-source-control-package"></a>Registrando com um pacote de controle do código-fonte
 Quando um arquivo em seu projeto é adicionado ao controle do código-fonte, o ambiente chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> para fornecer quatro cadeias de caracteres opacas que são usadas como cookies pelo sistema de controle do código-fonte. Armazene essas cadeias de caracteres em seu arquivo de projeto. Essas cadeias de caracteres devem ser passadas para o stub de controle do código-fonte (o componente do Visual Studio que gerencia os pacotes de controle do código-fonte) na inicialização do tipo de projeto chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A> . Isso, por sua vez, carrega o pacote de controle do código-fonte apropriado e encaminha a chamada para sua implementação do `IVsSccManager2::RegisterSccProject` .

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Suporte para controle do código-fonte](../../extensibility/internals/supporting-source-control.md)

---
title: Detalhes do Tempo de Execução do Controle de Fonte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 92ce5e822ec7360b3b1a4010d250a4349443c142
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705046"
---
# <a name="source-control-runtime-details"></a>Detalhes de runtime de controle do código-fonte
Um projeto é adicionado ao controle de origem quando o usuário adiciona um arquivo no projeto ao controle de origem, ou através de um controlador de automação, como um assistente. Um projeto não especifica por si mesmo que está sob controle de origem; suporta o controle de origem, mas deve ser adicionado manualmente.

## <a name="registering-with-a-source-control-package"></a>Registrando-se com um pacote de controle de origem
 Quando um arquivo em seu projeto é adicionado <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> ao controle de origem, o ambiente chama para fornecer quatro strings opacas que são usadas como cookies pelo sistema de controle de origem. Armazene essas strings no arquivo do projeto. Essas strings devem ser passadas para o Source Control Stub (o componente Visual Studio que <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>gerencia pacotes de controle de origem) na inicialização do tipo de projeto, chamando . Isso, por sua vez, carrega o pacote de controle `IVsSccManager2::RegisterSccProject`de origem apropriado e encaminha a chamada para a sua implementação de .

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Suporte para controle do código-fonte](../../extensibility/internals/supporting-source-control.md)

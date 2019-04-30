---
title: Eliminação de ~ SAK arquivos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96704b52fb31085fad7546687a8803c85bcfbb47
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63418636"
---
# <a name="elimination-of-sak-files"></a>Eliminação de ~ arquivos SAK
Na fonte de controle de plug-in API 1.2, o *~ SAK* arquivos foram substituídos por sinalizadores de recurso e dá suporte a plug-in de controle de novas funções de detectam se uma fonte de *MSSCCPRJ* de arquivo e check-outs compartilhados.

## <a name="sak-files"></a>~ Arquivos SAK
Visual Studio .NET 2003 criado prefixados com os arquivos temporários *~ SAK*. Esses arquivos são usados para determinar se um plug-in de controle de origem dá suporte a:

- O *Mssccprj* arquivo.

- Vários checkouts (compartilhados).

Para plug-ins que dão suporte a funções avançadas fornecidas a fonte de controle de plug-in API 1.2, o IDE pode detectar esses recursos sem criar os arquivos temporários com o uso de novos recursos, sinalizadores e funções, detalhadas nas seções a seguir.

## <a name="new-capability-flags"></a>Novos sinalizadores de recurso
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>Novas funções
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 Se um plug-in de controle de origem dá suporte a vários check-outs (compartilhados) e, em seguida, ele declara a `SCC_CAP_MULTICHECKOUT` funcionalidade e implementa o `SccIsMultiCheckOutEnabled` função. Essa função é chamada sempre que uma operação de check-out ocorre em qualquer um dos projetos de controle do código-fonte.

 Se um plug-in de controle de origem dá suporte à criação e ao uso de um *Mssccprj* do arquivo, em seguida, ele declara o `SCC_CAP_SCCFILE` funcionalidade e implementa os [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Essa função é chamada com uma lista de arquivos. A função retornará `TRUE' or 'FALSE` para cada arquivo indicar se o Visual Studio deve usar um *Mssccprj* arquivo para ele. Se o plug-in de controle do código-fonte optar por não dar suporte a esses novos recursos e funções, ele pode usar a seguinte chave do registro para desabilitar a criação desses arquivos:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]DoNotCreateTemporaryFilesInSourceControl** = *dword:00000001*

> [!NOTE]
> Se essa chave do registro for definida como *DWORD: 00000000*, é equivalente à chave que está sendo inexistente e Visual Studio ainda tenta criar arquivos temporários. No entanto, se a chave do registro for definida como *DWORD: 00000001*, Visual Studio não tentará criar arquivos temporários. Em vez disso, ele pressupõe que o plug-in de controle do código-fonte não dá suporte a *Mssccprj* de arquivo e não oferece suporte a check-outs compartilhados.

## <a name="see-also"></a>Consulte também
- [O que há de novo no controle de fonte de plug-in API versão 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
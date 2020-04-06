---
title: Eliminação de arquivos ~SAK | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0294198bb1560f8df6f17170013f88d4fe11e5cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708496"
---
# <a name="elimination-of-sak-files"></a>Eliminação de arquivos ~SAK
Na API 1.2 do Source Control Plug-in, os arquivos *~SAK* foram substituídos por sinalizadores de capacidade e novas funções que detectam se um plug-in de controle de origem suporta o arquivo *MSSCCPRJ* e checkouts compartilhados.

## <a name="sak-files"></a>~Arquivos SAK
O Visual Studio .NET 2003 criou arquivos temporários prefixados com *~SAK*. Esses arquivos são usados para determinar se um plug-in de controle de origem suporta:

- O arquivo *MSSCCPRJ.SCC.*

- Vários checkouts (compartilhados).

Para plug-ins que suportam funções avançadas fornecidas na API 1.2 do Plug-in de controle de fonte, o IDE pode detectar esses recursos sem criar os arquivos temporários através do uso de novos recursos, sinalizadores e funções, detalhados nas seções a seguir.

## <a name="new-capability-flags"></a>Novas bandeiras de capacidade
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>Novas funções
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 Se um plug-in de controle de origem suportar vários check-outs (compartilhados), ele declara a `SCC_CAP_MULTICHECKOUT` capacidade e implementa a `SccIsMultiCheckOutEnabled` função. Essa função é chamada sempre que ocorre uma operação de checkout em qualquer um dos projetos controlados por origem.

 Se um plug-in de controle de origem suportar a criação e o uso de um `SCC_CAP_SCCFILE` arquivo *MSSCCPRJ.SCC,* ele declara o recurso e implementa o [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Esta função é chamada com uma lista de arquivos. A função `TRUE' or 'FALSE` retorna para cada arquivo para indicar se o Visual Studio deve usar um arquivo *MSSCCPRJ.SCC* para ele. Se o plug-in de controle de origem optar por não suportar esses novos recursos e funções, ele poderá usar a seguinte chave de registro para desativar a criação desses arquivos:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] DoNotCreateTemporaryFilesInSourceControl** = *dword:00000001*

> [!NOTE]
> Se essa chave de registro estiver definida como *dword:000000000,* ela é equivalente à chave sendo inexistente, e o Visual Studio ainda tenta criar os arquivos temporários. No entanto, se a chave de registro estiver definida como *dword:00000001*, o Visual Studio não tentará criar os arquivos temporários. Em vez disso, assume que o plug-in de controle de origem não suporta o arquivo *MSSCCPRJ.SCC* e não suporta checkouts compartilhados.

## <a name="see-also"></a>Confira também
- [O que há de novo na API plug-in de controle de fonte versão 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

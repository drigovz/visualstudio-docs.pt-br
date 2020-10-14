---
title: Programando as Ferramentas do Visual Studio para Unity| Microsoft Docs
description: Consulte exemplos de programação usando a API de Ferramentas do Visual Studio para Unity (VSTU). Personalizar arquivos de projeto criados pelo VSTU. Compartilhe o retorno de chamada do log do Unity com VSTU.
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 0372cfd110df77867a683b27b17f92cd70ba75aa
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039879"
---
# <a name="program-visual-studio-tools-for-unity"></a>Programar as Ferramentas do Visual Studio para Unity
Nesta seção, você encontrará exemplos de como usar as Ferramentas do Visual Studio para API do Unity.

## <a name="examples"></a>Exemplos
 Aqui estão alguns exemplos que mostram como você pode usar as Ferramentas do Visual Studio para APIs do Unity.

### <a name="customize-project-files-created-by-vstu"></a>Personalizar arquivos de projeto criados pelo VSTU
 As ferramentas do Visual Studio para Unity fornecem um retorno de chamada de estilo Unity durante a geração do arquivo de projeto. Para saber como você pode modificar o arquivo de projeto sempre que ele é regenerado, confira [Exemplo: geração de arquivo de projeto](../cross-platform/customize-project-files-created-by-vstu.md).

### <a name="share-the-unity-log-callback-with-vstu"></a>Compartilhar o retorno de log do Unity com o VSTU
 As Ferramentas do Visual Studio para Unity registram um retorno de chamada de log do Unity para transmitir seu console para o Visual Studio. Se os scripts do seu editor também registram um retorno de chamada de log do Unity, o retorno de chamada VSTU pode interferir. Para saber como você pode compartilhar o retorno de chamada de log do Unity com VSTU, confira [Exemplo: retorno de chamada do log](../cross-platform/share-the-unity-log-callback-with-vstu.md).

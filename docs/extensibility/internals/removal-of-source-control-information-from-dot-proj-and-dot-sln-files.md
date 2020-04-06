---
title: Remover informações de controle de origem de arquivos .proj e .sln
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba3085a7806bfb0556613d1fca1b94953dcdb0b2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705583"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Remoção de informações de controle do código-fonte de arquivos .Proj e .Sln
Na versão 1.2 da API plug-in de controle de fonte, as informações do SCC são armazenadas em um MSSCCPRJ. Arquivo SCC. A vantagem do MSSCCPRJ. O arquivo SCC é que as informações do SCC não são controladas pela fonte, como em arquivos .proj e .sln.

## <a name="version-12-changes"></a>Alterações da versão 1.2
 Nos plug-ins de controle de origem baseados na versão 1.1 do Plug-in De controle de origem, as informações sobre o controle de origem são armazenadas nos arquivos project (.proj) e solução (.sln). A localização do banco de dados das informações de controle de origem é especificada pelo AuxPath, e o local específico dentro do banco de dados é especificado pelo ProjName. Esse comportamento pode causar problemas após operações de ramificação, garfo ou cópia, porque o ProjName normalmente seria inválido após qualquer uma dessas operações.

 Na versão 1.1 do Plug-in de controle de origem 1.1, o IDE usou arquivos ~SAK para detectar se um plug-in suportava o MSSCCPRJ. Método SCC de armazenar informações de controle de origem. A Versão 1.2 do Plug-in de Controle de Origem 1.2 fornece um novo recurso para detectar o suporte ao MSSCCPRJ. Arquivo SCC sem usar um arquivo ~SAK. Para obter mais informações, consulte [Eliminação de ~Arquivos SAK](../../extensibility/internals/elimination-of-tilde-sak-files.md).

## <a name="see-also"></a>Confira também
- [Novidades na API do plug-in de controle do código-fonte versão 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

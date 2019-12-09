---
title: Provedor de símbolo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65debb8fcb41bec1d42c82654c26bc7d19c04a67
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348514"
---
# <a name="symbol-provider"></a>Provedor de símbolos
Uma implementação do avaliador de expressão deve acessar as informações de depuração simbólica geradas pelo compilador de linguagem para avaliar as variáveis e expressões. Ele faz isso consome as interfaces de um provedor de símbolo (SP), também chamado de um manipulador de símbolo.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornece o SPs para código gerenciado, bem como código nativo usando o formato de arquivo de símbolo de banco de dados do programa (PDB). A menos que haja uma forte necessário para o seu programa usar símbolos armazenados em um formato personalizado, é recomendável que você use os SPs fornecidos pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="implementation-notes"></a>Observações sobre a implementação
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] esperam de mecanismos de depuração conversar com os SPs usando as interfaces do Common Language Runtime (CLR). Como resultado, um SP que estará trabalhando com os mecanismos de depuração do Visual Studio deve dar suporte o CLR. Uma lista completa de CLR de todas as interfaces de depuração pode ser encontrada em debugref.doc, que é parte do [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].

 Se sua SP trabalhar somente com o mecanismo de depuração personalizado, você pode implementar o SP como achar melhor dependendo das necessidades do seu mecanismo de depuração.

## <a name="see-also"></a>Consulte também
- [Componentes do depurador](../../extensibility/debugger/debugger-components.md)
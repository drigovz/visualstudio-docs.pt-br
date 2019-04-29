---
title: Provedor de símbolo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea31d6bcd8c055756a49c46f8fb4b3f377aaade8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912889"
---
# <a name="symbol-provider"></a>Provedor de símbolos
Uma implementação do avaliador de expressão deve acessar as informações de depuração simbólica geradas pelo compilador de linguagem para avaliar as variáveis e expressões. Ele faz isso consome as interfaces de um provedor de símbolo (SP), também chamado de um manipulador de símbolo.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornece o SPs para código gerenciado, bem como código nativo usando o formato de arquivo de símbolo de banco de dados do programa (PDB). A menos que haja uma forte necessário para o seu programa usar símbolos armazenados em um formato personalizado, é recomendável que você use os SPs fornecidos pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="implementation-notes"></a>Observações sobre a implementação
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] esperam de mecanismos de depuração conversar com os SPs usando as interfaces do Common Language Runtime (CLR). Como resultado, um SP que estará trabalhando com os mecanismos de depuração do Visual Studio deve dar suporte o CLR. Uma lista completa de CLR de todas as interfaces de depuração pode ser encontrada em debugref.doc, que é parte do [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].

 Se sua SP trabalhar somente com o mecanismo de depuração personalizado, você pode implementar o SP como achar melhor dependendo das necessidades do seu mecanismo de depuração.

## <a name="see-also"></a>Consulte também
- [Componentes do depurador](../../extensibility/debugger/debugger-components.md)
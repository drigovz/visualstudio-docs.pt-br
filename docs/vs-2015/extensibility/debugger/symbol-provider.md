---
title: Provedor de símbolo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6af1af9d2e178241fa8a5957e18c1a5333fa4b09
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68178895"
---
# <a name="symbol-provider"></a>Provedor de símbolo
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Uma implementação do avaliador de expressão deve acessar as informações de depuração simbólica geradas pelo compilador de linguagem para avaliar as variáveis e expressões. Ele faz isso consome as interfaces de um provedor de símbolo (SP), também chamado de um manipulador de símbolo.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fornece o SPs para código gerenciado, bem como código nativo usando o formato de arquivo de símbolo de banco de dados do programa (PDB). A menos que haja uma forte necessário para o seu programa usar símbolos armazenados em um formato personalizado, é recomendável que você use os SPs fornecidos pelo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="implementation-notes"></a>Notas de implementação  
 O [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] esperam de mecanismos de depuração conversar com os SPs usando as interfaces do Common Language Runtime (CLR). Como resultado, um SP que estará trabalhando com os mecanismos de depuração do Visual Studio deve dar suporte o CLR. Uma lista completa de CLR de todas as interfaces de depuração pode ser encontrada em debugref.doc, que é parte do [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)].  
  
 Se sua SP trabalhar somente com o mecanismo de depuração personalizado, você pode implementar o SP como achar melhor dependendo das necessidades do seu mecanismo de depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Componentes do depurador](../../extensibility/debugger/debugger-components.md)

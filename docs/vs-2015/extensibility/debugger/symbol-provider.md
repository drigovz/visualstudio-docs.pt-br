---
title: Provedor de símbolos | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178895"
---
# <a name="symbol-provider"></a>Provedor de símbolo
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Uma implementação do avaliador de expressão deve acessar as informações de depuração simbólicas geradas pelo compilador de linguagem para avaliar variáveis e expressões. Ele faz isso consumindo as interfaces de um provedor de símbolo (SP), também chamado de manipulador de símbolo.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fornece o SPs para código gerenciado, bem como código nativo usando o formato de arquivo de símbolo do banco de dados do programa (PDB). A menos que haja uma forte necessidade de o programa usar símbolos armazenados em um formato personalizado, é recomendável que você use os SPs fornecidos pelo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="implementation-notes"></a>Notas da implementação  
 Os [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mecanismos de depuração esperam se comunicar com o SPS usando interfaces CLR (Common Language Runtime). Como resultado, um SP que estará trabalhando com os mecanismos de depuração do Visual Studio deve dar suporte ao CLR. Uma lista completa de todas as interfaces de depuração CLR pode ser encontrada em debugref.doc, que faz parte do [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)] .  
  
 Se o SP estiver funcionando apenas com o mecanismo de depuração personalizado, você poderá implementar o SP, como se desejar, dependendo das necessidades do mecanismo de depuração.  
  
## <a name="see-also"></a>Consulte Também  
 [Componentes do depurador](../../extensibility/debugger/debugger-components.md)

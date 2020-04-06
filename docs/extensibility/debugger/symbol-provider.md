---
title: Provedor de Símbolos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b90846d9494ee046cf9dc4a3e5de9ff033ea3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712814"
---
# <a name="symbol-provider"></a>Provedor de símbolos
Uma implementação avaliadora de expressão deve acessar as informações simbólicas de depuração geradas pelo compilador de idiomas para avaliar variáveis e expressões. Ele faz isso consumindo as interfaces de um provedor de símbolos (SP), também chamado de manipulador de símbolos.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fornece SPs para código gerenciado, bem como código nativo usando o formato de arquivo de símbolo Program DataBase (PDB). A menos que haja uma forte necessidade de seu programa usar símbolos armazenados em um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]formato personalizado, é recomendável que você use os SPs fornecidos por .

## <a name="implementation-notes"></a>Notas de implementação
 Os [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motores de depuração esperam conversar com os SPs usando interfaces CLR (Common Language Runtime). Como resultado, uma SP que estará trabalhando com os motores de depuração do Visual Studio deve suportar o CLR. Uma lista completa de todas as interfaces de depuração CLR pode ser [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]encontrada em debugref.doc, que faz parte do .

 Se o seu SP estiver funcionando apenas com o seu motor de depuração personalizado, você pode implementar a SP como achar melhor, dependendo das necessidades do seu motor de depuração.

## <a name="see-also"></a>Confira também
- [Componentes do depurador](../../extensibility/debugger/debugger-components.md)

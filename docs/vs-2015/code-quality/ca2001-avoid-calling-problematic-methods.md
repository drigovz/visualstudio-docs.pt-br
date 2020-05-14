---
title: 'CA2001: evite chamar métodos problemáticos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 318b7b8adddd674a9b8ecb93441d69a76ab574dd
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586778"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: Evitar chamar métodos problemáticos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|Categoria|Microsoft. confiabilidade|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um membro chama um método potencialmente perigoso ou problemático.

## <a name="rule-description"></a>Descrição da Regra
 Evite fazer chamadas de método desnecessárias e potencialmente perigosas.

 Uma violação dessa regra ocorre quando um membro chama um dos métodos a seguir.

|Método|Descrição|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Chamando GC. A coleta pode afetar significativamente o desempenho do aplicativo e raramente é necessária. Para obter mais informações, consulte a entrada de blog [palhinhas de desempenho do rico Mariani](https://docs.microsoft.com/archive/blogs/ricom/when-to-call-gc-collect) no msdn.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread. Suspend e thread. resume foram preteridos devido ao comportamento imprevisível.  Use <xref:System.Threading> outras classes no namespace, como <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>e <xref:System.Threading.Semaphore> para sincronizar threads ou proteger recursos.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|O método DangerousGetHandle representa um risco de segurança porque ele pode retornar um identificador que não é válido. Consulte os <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> métodos e para obter mais informações sobre como usar o método DangerousGetHandle com segurança.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Esses métodos podem carregar assemblies de locais inesperados. Por exemplo, consulte blog do .NET CLR Notes do Suzanne Cook posta [LoadFile vs. LoadFrom](https://docs.microsoft.com/archive/blogs/suzcook/loadfile-vs-loadfrom) e [escolhendo um contexto de associação](https://docs.microsoft.com/archive/blogs/suzcook/choosing-a-binding-context) no site do MSDN para obter informações sobre métodos que carregam assemblies.|
|[CoSetProxyBlanket](https://msdn.microsoft.com/library/ms692692.aspx) (Ole32)<br /><br /> [CoInitializeSecurity](https://msdn.microsoft.com/library/ms693736.aspx) (Ole32)|No momento em que o código do usuário começa a ser executado em um processo gerenciado, ele é muito tarde para chamar CoSetProxyBlanket com confiança. O Common Language Runtime (CLR) usa ações de inicialização que podem impedir que os usuários P/Invoke tenham sucesso.<br /><br /> Se você precisar chamar CoSetProxyBlanket para um aplicativo gerenciado, recomendamos que inicie o processo usando um executável de código nativo (C++), chame CoSetProxyBlanket no código nativo e, em seguida, inicie o aplicativo de código gerenciado em andamento. (Certifique-se de especificar um número de versão de tempo de execução.)|

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, remova ou substitua a chamada para o método perigoso ou problemático.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Você deve suprimir as mensagens desta regra somente quando nenhuma alternativa ao método problemático estiver disponível.

## <a name="see-also"></a>Consulte Também
 [Avisos de confiabilidade](../code-quality/reliability-warnings.md)

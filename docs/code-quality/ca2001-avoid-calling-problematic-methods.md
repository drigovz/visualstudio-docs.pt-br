---
title: 'CA2001: Evitar chamar métodos problemáticos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 95209067f3821b6446b64dc7990e189720d20cea
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233188"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: Evitar chamar métodos problemáticos

|||
|-|-|
|NomeDoTipo|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|Categoria|Microsoft.Reliability|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um membro chama um método potencialmente perigoso ou problemático.

## <a name="rule-description"></a>Descrição da regra

Evite fazer chamadas de método desnecessárias e potencialmente perigosas. Uma violação dessa regra ocorre quando um membro chama um dos seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Chamando GC. A coleta pode afetar significativamente o desempenho do aplicativo e raramente é necessária. Para obter mais informações, consulte a entrada [de blog palhinhas de desempenho de rico Mariani](http://go.microsoft.com/fwlink/?LinkId=169256) no msdn.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread. Suspend e thread. resume foram preteridos devido ao comportamento imprevisível.  Use <xref:System.Threading> outras classes no namespace, <xref:System.Threading.Monitor>como, <xref:System.Threading.Mutex>e <xref:System.Threading.Semaphore>, para sincronizar threads ou proteger recursos.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|O método DangerousGetHandle representa um risco de segurança porque ele pode retornar um identificador que não é válido. Consulte os <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> métodos e para obter mais informações sobre como usar o método DangerousGetHandle com segurança.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Esses métodos podem carregar assemblies de locais inesperados. Por exemplo, consulte blog [de observações sobre o .NET CLR Notes do Suzanne vs. LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450) e [escolhendo um contexto de associação](http://go.microsoft.com/fwlink/?LinkId=164451) para obter informações sobre métodos que carregam assemblies.|
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) (Ole32)<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) Ole32|No momento em que o código do usuário começa a ser executado em um processo gerenciado, ele é muito tarde para chamar CoSetProxyBlanket com confiança. O Common Language Runtime (CLR) usa ações de inicialização que podem impedir que os usuários P/Invoke tenham sucesso.<br /><br /> Se você precisar chamar CoSetProxyBlanket para um aplicativo gerenciado, recomendamos que inicie o processo usando um executável de código nativo (C++), chame CoSetProxyBlanket no código nativo e, em seguida, inicie o aplicativo de código gerenciado em andamento. (Certifique-se de especificar um número de versão de tempo de execução.)|

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, remova ou substitua a chamada para o método perigoso ou problemático.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Você deve suprimir as mensagens desta regra somente quando nenhuma alternativa ao método problemático estiver disponível.

## <a name="see-also"></a>Consulte também

- [Avisos de confiabilidade](../code-quality/reliability-warnings.md)
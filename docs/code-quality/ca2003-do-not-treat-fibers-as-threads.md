---
title: 'CA2003: Não tratar fibras como threads'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f5e4e7eb28207cb37824b23acbbac02b6df380d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233142"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: Não tratar fibras como threads

|||
|-|-|
|NomeDoTipo|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|Categoria|Microsoft.Reliability|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um thread gerenciado está sendo tratado como um Thread Win32.

## <a name="rule-description"></a>Descrição da regra

Não presuma que um thread gerenciado seja um Thread Win32; é uma fibra. O Common Language Runtime (CLR) executa threads gerenciados como fibras no contexto de threads reais que são de Propriedade do SQL. Esses threads podem ser compartilhados entre AppDomains e até mesmo bancos de dados no processo de SQL Server. O uso do armazenamento local de threads gerenciados funciona, mas você não pode usar o armazenamento local de thread não gerenciado ou supor que seu código será executado no thread do sistema operacional atual novamente. Não altere as configurações, como a localidade do thread. Não chame CreateCriticalSection ou CreateMutex via P/Invoke porque eles exigem que o thread que entra em um bloqueio também deva sair do bloqueio. Como o thread que entra em um bloqueio não sai de um bloqueio quando você usa fibras, as seções críticas e mutexes do Win32 são inúteis no SQL. Você pode usar com segurança a maior parte do estado em um <xref:System.Threading.Thread> objeto gerenciado, incluindo o armazenamento local de threads gerenciados e a cultura da interface do usuário (IU) atual do thread. No entanto, para fins de modelo de programação, você não poderá alterar a cultura atual de um thread ao usar o SQL. Essa limitação será imposta por meio de uma nova permissão.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Examine seu uso de threads e altere seu código de acordo.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprimir esta regra.
---
title: 'CA2006: Usar SafeHandle para encapsular recursos nativos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 0e671deab060346bb998932495e5590f19945eaa
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233096"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: Usar SafeHandle para encapsular recursos nativos

|||
|-|-|
|NomeDoTipo|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Categoria|Microsoft.Reliability|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

O código gerenciado <xref:System.IntPtr> usa o para acessar recursos nativos.

## <a name="rule-description"></a>Descrição da regra

O uso `IntPtr` do em código gerenciado pode indicar um problema de segurança e confiabilidade em potencial. Todos os usos `IntPtr` do devem ser revisados para determinar se o <xref:System.Runtime.InteropServices.SafeHandle> uso de uma tecnologia, ou semelhante, é necessário em seu lugar. Ocorrerão problemas se o `IntPtr` representar algum recurso nativo, como memória, um identificador de arquivo ou um soquete, que o código gerenciado é considerado proprietário. Se o código gerenciado possui o recurso, ele também deve liberar os recursos nativos associados a ele, pois uma falha ao fazer isso causaria o vazamento de recursos.

Nesses cenários, problemas de segurança ou confiabilidade também existirão se o acesso multithread for permitido para o `IntPtr` e uma maneira de liberar o recurso que é representado `IntPtr` pelo for fornecido. Esses problemas envolvem a `IntPtr` reciclagem do valor na liberação de recursos enquanto o uso simultâneo do recurso está sendo feito em outro thread. Isso pode causar condições de corrida em que um thread pode ler ou gravar dados associados ao recurso errado. Por exemplo, se o seu tipo armazena um identificador de sistema `IntPtr` operacional como um e permite que os usuários chamem o **fechamento** e qualquer outro método que usa esse identificador simultaneamente e sem algum tipo de sincronização, seu código tem um problema de reciclagem de identificador.

Esse problema de reciclagem de identificador pode causar corrupção de dados e, frequentemente, uma vulnerabilidade de segurança. `SafeHandle`e sua classe <xref:System.Runtime.InteropServices.CriticalHandle> irmã fornece um mecanismo para encapsular um identificador nativo para um recurso para que tais problemas de Threading possam ser evitados. Além disso, você pode `SafeHandle` usar e sua classe `CriticalHandle` irmã para outros problemas de Threading, por exemplo, para controlar cuidadosamente o tempo de vida de objetos gerenciados que contêm uma cópia do identificador nativo em chamadas para métodos nativos. Nessa situação, muitas vezes você pode remover chamadas para `GC.KeepAlive`. A sobrecarga de desempenho que você incorre ao `SafeHandle` usar e, para um menor grau `CriticalHandle`,, muitas vezes, pode ser reduzida por meio de um design cuidadoso.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Converta `IntPtr` o `SafeHandle` uso para para gerenciar com segurança o acesso a recursos nativos. Consulte o <xref:System.Runtime.InteropServices.SafeHandle> artigo de referência para obter exemplos.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprimir este aviso.

## <a name="see-also"></a>Consulte também

- <xref:System.IDisposable>
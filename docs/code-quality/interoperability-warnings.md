---
title: Avisos de interoperabilidade
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e18b8ccbdc688586004a363f16360ace1bb488c9
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78167592"
---
# <a name="interoperability-warnings"></a>Avisos de interoperabilidade

Os avisos de interoperabilidade dão suporte à interação com clientes COM.

## <a name="in-this-section"></a>Nesta seção

| Regra | DESCRIÇÃO |
| - | - |
| [CA1400: os pontos de entrada de P-Invoke devem existir](../code-quality/ca1400.md) | Um método público ou protegido é marcado usando-se o atributo System.Runtime.InteropServices.DllImportAttribute. Não foi possível localizar a biblioteca não gerenciada ou não foi possível comparar o método a uma função na biblioteca. |
| [CA1401: os P/Invokes não devem estar visíveis](../code-quality/ca1401.md) | Um método público ou protegido em um tipo público tem o atributo System. Runtime. InteropServices. DllImportAttribute (também implementado pela palavra-chave declare no Visual Basic). Esses métodos não devem ser expostos. |
| [CA1402: evitar sobrecargas em interfaces visíveis em COM](../code-quality/ca1402.md) | Quando os métodos sobrecarregados são expostos a clientes COM, apenas a primeira sobrecarga do método mantém seu nome. As sobrecargas subsequentes são renomeadas com exclusividade acrescentando-se ao nome um caractere de sublinhado (_) e um inteiro correspondente à ordem de declaração da sobrecarga. |
| [CA1403: os tipos de layout automático não devem ser visíveis em COM](../code-quality/ca1403.md) | Um tipo de valor visível COM é marcado usando o atributo System. Runtime. InteropServices. StructLayoutAttribute definido como LayoutKind. auto. O layout desses tipos pode ser alterado entre as versões do .NET, o que interromperá clientes COM que esperam um layout específico. |
| [CA1404: chamar GetLastError logo depois de P/Invoke](../code-quality/ca1404.md) | É feita uma chamada para o método Marshal. GetLastWin32Error ou o equivalente [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] função GetLastError, e a chamada imediatamente anterior não é um método de invocação de plataforma. |
| [CA1405: os tipos base de tipo visível em COM devem ser visíveis em COM](../code-quality/ca1405.md) | Um tipo visível por COM deriva de um tipo que não é visível por COM. |
| [CA1406: evitar argumentos Int64 para clientes do Visual Basic 6](../code-quality/ca1406.md) | Os clientes COM do Visual Basic 6 não podem acessar inteiros de 64 bits. |
| [CA1407: evitar membros estáticos em tipos visíveis em COM](../code-quality/ca1407.md) | COM não dá suporte para métodos estáticos. |
| [CA1408: não usar AutoDual ClassInterfaceType](../code-quality/ca1408.md) | Tipos que usam uma interface dupla permitem que clientes sejam associados a um layout de interface específico. Todas as alterações feitas em uma versão futura do layout do tipo ou de qualquer tipo de base interromperão clientes COM associados à interface. Por padrão, se o atributo ClassInterfaceAttribute não for especificado, será usada uma interface somente de expedição. |
| [CA1409: os tipos visíveis em Com devem ser criáveis](../code-quality/ca1409.md) | Um tipo de referência marcado especificamente como visível para COM contém um construtor parametrizado público, mas não contém um construtor padrão público (sem parâmetros). Um tipo sem um construtor padrão público não pode ser criado por clientes COM. |
| [CA1410: os métodos de registro COM devem ser correspondentes](../code-quality/ca1410.md) | Um tipo declara um método que é marcado usando o atributo <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>, mas não declara um método que é marcado usando o atributo <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>, ou vice-versa. |
| [CA1411: os métodos de registro COM não devem estar visíveis](../code-quality/ca1411.md) | Um método que é marcado usando o atributo System. Runtime. InteropServices. ComRegisterFunctionAttribute ou o atributo System. Runtime. InteropServices. ComUnregisterFunctionAttribute é visível externamente. |
| [CA1412: marcar interfaces ComSource como IDispatch](../code-quality/ca1412.md) | Um tipo é marcado usando-se o atributo System.Runtime.InteropServices.ComSourceInterfacesAttribute, e pelo menos uma das interfaces especificadas não está marcada usando-se o atributo System.Runtime.InteropServices.InterfaceTypeAttribute definido como ComInterfaceType.InterfaceIsIDispatch. |
| [CA1413: evitar campos não públicos em tipos de valor visíveis em COM](../code-quality/ca1413.md) | Os campos de instância não pública dos tipos de valor visíveis por COM permanecem visíveis para clientes COM. Revise o conteúdo dos campos em busca de informações que não devem ser expostas, ou isso terá efeitos não intencionais sobre o design ou a segurança. |
| [CA1414: marcar argumentos P/Invoke boolianos com MarshalAs](../code-quality/ca1414.md) | O tipo de dados Booliano tem várias representações em código não gerenciado. |
| [CA1415: declarar P/Invokes corretamente](../code-quality/ca1415.md) | Essa regra procura declarações de método de invocação de plataforma que se destinam a [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] funções que têm um ponteiro para um parâmetro de estrutura SOBREPOSTA e o parâmetro gerenciado correspondente não é um ponteiro para uma estrutura de <xref:System.Threading.NativeOverlapped?displayProperty=fullName>. |

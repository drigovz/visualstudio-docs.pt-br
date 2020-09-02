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
ms.openlocfilehash: 74bffffa2b4f95aeab20438199bb19693a1a3b94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87235115"
---
# <a name="interoperability-warnings"></a>Avisos de interoperabilidade

Os avisos de interoperabilidade dão suporte à interação com clientes COM.

## <a name="in-this-section"></a>Nesta seção

| Regra | Descrição |
| - | - |
| [CA1400: os pontos de entrada P/Invoke devem existir](../code-quality/ca1400.md) | Um método público ou protegido é marcado usando-se o atributo System.Runtime.InteropServices.DllImportAttribute. Não foi possível localizar a biblioteca não gerenciada ou não foi possível comparar o método a uma função na biblioteca. |
| [CA1401: P/Invokes não devem estar visíveis](../code-quality/ca1401.md) | Um método público ou protegido em um tipo público tem o atributo System.Runtime.InteropServices.DllImportAttribute (também implementado pela palavra-chave declare em Visual Basic). Esses métodos não devem ser expostos. |
| [CA1402: Evitar sobrecargas em interfaces visíveis no COM](../code-quality/ca1402.md) | Quando os métodos sobrecarregados são expostos a clientes COM, apenas a primeira sobrecarga do método mantém seu nome. As sobrecargas subsequentes são renomeadas com exclusividade acrescentando-se ao nome um caractere de sublinhado (_) e um inteiro correspondente à ordem de declaração da sobrecarga. |
| [CA1403: Tipos de layout automático não devem ser visíveis no COM](../code-quality/ca1403.md) | Um tipo de valor visível COM é marcado usando o atributo System. Runtime. InteropServices. StructLayoutAttribute definido como LayoutKind. auto. O layout desses tipos pode ser alterado entre as versões do .NET, o que interromperá clientes COM que esperam um layout específico. |
| [CA1404: chamar GetLastError imediatamente após P/Invoke](../code-quality/ca1404.md) | É feita uma chamada para o método Marshal. GetLastWin32Error ou a [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] função GetLastError equivalente, e a chamada imediatamente anterior não é para um método de invocação de plataforma. |
| [CA1405: Tipos base de tipo visível no COM devem ser visíveis no COM](../code-quality/ca1405.md) | Um tipo visível por COM deriva de um tipo que não é visível por COM. |
| [CA1406: Evitar argumentos Int64 para clientes do Visual Basic 6](../code-quality/ca1406.md) | Os clientes COM do Visual Basic 6 não podem acessar inteiros de 64 bits. |
| [CA1407: Evitar membros estáticos em tipos visíveis no COM](../code-quality/ca1407.md) | COM não dá suporte para métodos estáticos. |
| [CA1408: Não usar AutoDual ClassInterfaceType](../code-quality/ca1408.md) | Tipos que usam uma interface dupla permitem que clientes sejam associados a um layout de interface específico. Todas as alterações feitas em uma versão futura do layout do tipo ou de qualquer tipo de base interromperão clientes COM associados à interface. Por padrão, se o atributo ClassInterfaceAttribute não for especificado, será usada uma interface somente de expedição. |
| [CA1409: Tipos visíveis no COM devem poder ser criados](../code-quality/ca1409.md) | Um tipo de referência marcado especificamente como visível para COM contém um construtor parametrizado público, mas não contém um construtor padrão público (sem parâmetros). Um tipo sem um construtor padrão público não pode ser criado por clientes COM. |
| [CA1410: Métodos de registro COM devem ser correspondidos](../code-quality/ca1410.md) | Um tipo declara um método que é marcado usando o atributo, <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> mas não declara um método que é marcado usando o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributo ou vice-versa. |
| [CA1411: Métodos de registro COM não devem ser visíveis](../code-quality/ca1411.md) | Um método que é marcado usando o atributo System. Runtime. InteropServices. ComRegisterFunctionAttribute ou o atributo System. Runtime. InteropServices. ComUnregisterFunctionAttribute é visível externamente. |
| [CA1412: Marcar interfaces ComSource como IDispatch](../code-quality/ca1412.md) | Um tipo é marcado usando-se o atributo System.Runtime.InteropServices.ComSourceInterfacesAttribute, e pelo menos uma das interfaces especificadas não está marcada usando-se o atributo System.Runtime.InteropServices.InterfaceTypeAttribute definido como ComInterfaceType.InterfaceIsIDispatch. |
| [CA1413: Evitar campos não públicos em tipos de valor visíveis no COM](../code-quality/ca1413.md) | Os campos de instância não pública dos tipos de valor visíveis por COM permanecem visíveis para clientes COM. Revise o conteúdo dos campos em busca de informações que não devem ser expostas, ou isso terá efeitos não intencionais sobre o design ou a segurança. |
| [CA1414: marcar argumentos P/Invoke boolianos com MarshalAs](../code-quality/ca1414.md) | O tipo de dados Booliano tem várias representações em código não gerenciado. |
| [CA1415: declarar P/Invokes corretamente](../code-quality/ca1415.md) | Essa regra procura declarações de método de invocação de plataforma que se destinam a [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] funções que têm um ponteiro para um parâmetro de estrutura Sobreposto e o parâmetro gerenciado correspondente não é um ponteiro para uma <xref:System.Threading.NativeOverlapped?displayProperty=fullName> estrutura. |
| [CA1417: não usar `OutAttribute` em parâmetros de cadeia de caracteres para P/Invokes](../code-quality/ca1417.md) | Parâmetros de cadeia de caracteres passados por valor com o `OutAttribute` podem desestabilizar o tempo de execução se a cadeia de caracteres for uma cadeia de caracteres interna. |
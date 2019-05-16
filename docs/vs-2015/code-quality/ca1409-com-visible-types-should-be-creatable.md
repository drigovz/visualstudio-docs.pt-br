---
title: 'CA1409: Tipos visíveis com devem ser criáveis | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7bd52ad75c67f9c8faa80e84eb5ae09c22c25280
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65678872"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: Tipos visíveis no COM devem poder ser criados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Categoria|Microsoft.Interoperability|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Um tipo de referência marcado especificamente como visível para COM Component Object Model () contém um construtor parametrizado público, mas não contém um construtor público padrão (sem parâmetros).

## <a name="rule-description"></a>Descrição da Regra
 Um tipo sem um construtor padrão público não pode ser criado por clientes COM. No entanto, o tipo ainda pode ser acessado por clientes COM se houver outros meios criar o tipo e passá-lo para o cliente (por exemplo, por meio de obter o valor retornado de uma chamada de método).

 A regra sempre ignora os tipos que são derivados de <xref:System.Delegate?displayProperty=fullName>.

 Por padrão, a seguir é visível no COM: assemblies, tipos públicos, membros de instância pública em tipos públicos e todos os membros de tipos de valor público.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, adicione um construtor padrão público ou remova o <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> do tipo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso nessa regra, se outros modos são fornecidos para criar e passar o objeto para o cliente COM.

## <a name="related-rules"></a>Regras relacionadas
 [CA1017: Marcar assemblies com ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Consulte também
 [Qualificando tipos do .NET para interoperação](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [interoperação com código não gerenciado](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)

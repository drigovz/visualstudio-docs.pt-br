---
title: 'CA2238: Implementar métodos de serialização corretamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
helpviewer_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cff617adf2b31ef773de3bc41db7245346795bee
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59657123"
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238: Implementar métodos de serialização corretamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para a documentação mais recente do Visual Studio, consulte [CA2238: Implementar métodos de serialização corretamente](https://docs.microsoft.com/visualstudio/code-quality/ca2238-implement-serialization-methods-correctly).  
  
|||  
|-|-|  
|NomeDoTipo|ImplementSerializationMethodsCorrectly|  
|CheckId|CA2238|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Quebrando - se o método é visível fora do assembly.<br /><br /> Sem quebra - se o método não é visível fora do assembly.|  
  
## <a name="cause"></a>Causa  
 Um método que trata um evento de serialização não tem a assinatura, o tipo de retorno ou a visibilidade corretos.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Um método é designado um manipulador de eventos de serialização, aplicando um dos seguintes atributos de evento de serialização:  
  
- <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>  
  
- <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>  
  
- <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>  
  
- <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>  
  
  Manipuladores de eventos de serialização usam um único parâmetro do tipo <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, return `void`e ter `private` visibilidade.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação dessa regra, corrija a assinatura, o tipo de retorno ou a visibilidade do manipulador de eventos de serialização.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra a serialização declarada corretamente manipuladores de eventos.  
  
 [!code-csharp[FxCop.Usage.SerializationEventHandlers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/cs/FxCop.Usage.SerializationEventHandlers.cs#1)]
 [!code-vb[FxCop.Usage.SerializationEventHandlers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/vb/FxCop.Usage.SerializationEventHandlers.vb#1)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA2236: Chamar métodos da classe base em tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: Implementar ISerializable corretamente](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2235: Marcar todos os campos não serializáveis](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: Marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Fornecer métodos de desserialização para campos opcionais](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Construtores de serialização segura](../code-quality/ca2120-secure-serialization-constructors.md)

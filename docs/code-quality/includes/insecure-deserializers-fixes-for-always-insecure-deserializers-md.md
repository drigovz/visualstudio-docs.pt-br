---
author: dotpaul
ms.author: paulming
ms.date: 05/01/2019
ms.topic: include
ms.openlocfilehash: bc423f10cfbae0b7a0cdaedb72f6891a0e12d228
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68147105"
---
- Se possível, use um serializador seguro em vez disso, e **não permitir que um invasor especificar um tipo arbitrário para desserializar**. Alguns serializadores mais seguros incluem:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -Nunca usar <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Se você precisar usar um resolvedor de tipo, restringir tipos desserializados para uma lista de esperado.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET - TypeNameHandling.None de uso. Se você precisar usar outro valor para TypeNameHandling, restringir tipos desserializados para uma lista de esperado com um ISerializationBinder personalizado.
  - Buffers de protocolo
- Verifique a prova de adulteração de dados serializados. Após a serialização, assina criptograficamente os dados serializados. Antes de desserialização, valide a assinatura de criptografia. Protege a chave de criptografia do que está sendo divulgadas e design para rotações de chave.
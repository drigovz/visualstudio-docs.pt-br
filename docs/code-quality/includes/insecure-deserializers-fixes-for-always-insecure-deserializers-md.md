---
author: dotpaul
ms.author: paulming
ms.date: 05/01/2019
ms.topic: include
ms.openlocfilehash: bc423f10cfbae0b7a0cdaedb72f6891a0e12d228
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89323544"
---
- Se possível, use um serializador seguro em vez disso e **não permita que um invasor especifique um tipo arbitrário para desserializar**. Alguns serializadores mais seguros incluem:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -Nunca use <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType> . Se você precisar usar um resolvedor de tipo, restrinja os tipos desserializados a uma lista esperada.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET-use TypeNameHandling. None. Se você precisar usar outro valor para TypeNameHandling, restrinja os tipos desserializados a uma lista esperada com um ISerializationBinder personalizado.
  - Buffers de protocolo
- Torne a prova de adulteração dos dados serializados. Após a serialização, assine criptograficamente os dados serializados. Antes da desserialização, valide a assinatura criptográfica. Proteja a chave de criptografia de ser divulgada e design para rotações de chave.
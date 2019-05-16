---
title: 'Como: Criar um esquema XML de um documento XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a732f0c6a9758de3ebd918559203b13a56d6a0ae
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697797"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Como: Criar um esquema XML de um documento XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O Editor de XML permite que você crie uma linguagem XSD (definição de esquema XML) de um documento XML. O documento de instância XML determina como o esquema é gerado da seguinte maneira:  
  
- Se o documento XML não tiver nenhum esquema ou DTD (definição de tipo de documento) associado a ele, os dados no documento XML serão usados para inferir um novo esquema XML.  
  
- Se o documento XML contiver um DTD associado, o DTD externo e o subconjunto interno serão convertidos em um esquema XML correspondente.  
  
- Se o documento XML contiver dados internos com um esquema XDR reduzido de dados XML, o esquema XDR será convertido em um esquema XML correspondente.  
  
  Os esquemas que são criados são, em seguida, usados para fornecer o IntelliSense para o documento XML.  
  
  Para obter mais informações sobre o mecanismo de inferência de esquema, consulte [inferindo um esquema XML](https://msdn.microsoft.com/library/b18e7ffd-3c04-482d-9934-ba2f6a59b2c9).  
  
### <a name="to-create-an-xml-schema"></a>Para criar um esquema XML  
  
1. Carregue um documento de instância XML no Editor de XML.  
  
2. Clique o **Create Schema** botão da **barra de ferramentas**.  
  
     Um documento de esquema XML é criado e aberto para cada namespace encontrado no documento de instância XML. Cada esquema é aberto como um arquivo variado temporário.  
  
     Os esquemas podem ser salvos no disco, adicionados ao seu projeto ou descartados.  
  
    > [!NOTE]
    > O **Create Schema** comando também está disponível no menu de atalho do Editor de XML e, nas **XML** menu.  
  
## <a name="see-also"></a>Consulte também  
 [Editor de XML](../xml-tools/xml-editor.md)

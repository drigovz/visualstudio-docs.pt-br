---
title: Criar um esquema XML
description: Saiba como usar o editor de XML no Visual Studio para criar um esquema XSD (linguagem de definição de esquema XML) a partir de um documento XML.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e33a4add7ebc6a3e323331731f3183d7a0dce26f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970277"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Como: criar um esquema XML a partir de um documento XML

O editor de XML permite que você crie um esquema XSD (linguagem de definição de esquema XML) a partir de um documento XML. O arquivo XML determina como o esquema é gerado da seguinte maneira:

- Se o documento XML não tiver nenhum esquema ou DTD (definição de tipo de documento) associado a ele, os dados no documento XML serão usados para inferir um novo esquema XML.

- Se o documento XML contiver um DTD associado, o DTD externo e o subconjunto interno serão convertidos em um esquema XML correspondente.

- Se o documento XML contiver dados internos com um esquema XDR reduzido de dados XML, o esquema XDR será convertido em um esquema XML correspondente.

Os esquemas que são criados são usados para fornecer o IntelliSense para o arquivo XML.

Para obter mais informações sobre o mecanismo de inferência de esquema, consulte [inferir um esquema XML](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Para criar um esquema XML

1. Abra um arquivo XML no Visual Studio.

2. Na barra de menus, escolha **XML**  >  **criar esquema**.

   Um documento de esquema XML é criado e aberto para cada namespace encontrado no arquivo XML. Cada esquema é aberto como um arquivo variado temporário. Os esquemas podem ser salvos no disco, adicionados ao seu projeto ou descartados.

## <a name="see-also"></a>Consulte também

- [Editor de XML](../xml-tools/xml-editor.md)

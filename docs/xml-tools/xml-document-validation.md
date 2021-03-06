---
title: Validação de documento XML no editor de XML
description: Saiba mais sobre a validação de documento XML no editor de XML e como ele verifica a sintaxe XML 1,0 e executa a validação de dados conforme você digita.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3d7046a08ac61ac0c23e98a47fb5eda75e38846c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874997"
---
# <a name="xml-document-validation"></a>Validação de documento XML

O editor de XML verifica a sintaxe XML 1,0 e também executa a validação de dados conforme você digita. O editor pode validar usando uma DTD (definição de tipo de documento) ou um esquema. Os sublinhados ondulados vermelhos realçam todos os erros de XML 1.0 bem-formado. Os sublinhados ondulados azuis mostram os erros semânticos com base na validação de DTD ou de esquema. Cada erro tem uma entrada associada na lista de erros. Você também pode exibir a mensagem de erro pausando o mouse sobre o sublinhado ondulado.

Os esquemas usados na validação são encontrados correspondendo o `targetNamespace` de um esquema compilado com a declaração xmlns do elemento. Os esquemas compilados são carregados de um dos seguintes locais, listados por ordem de prioridade:

- Do nome de arquivo especificado no campo **esquemas** da janela **Propriedades** do documento.

- Um esquema ou DTD embutido.

- Uma DTD externa ou os atributos `xsd:schemaLocation` e `xsd:noNamespaceSchemaLocation`

- Um URI de um namespace do esquema XDR "x-schema".

Os esquemas também podem ser encontrados nos seguintes locais adicionais quando o esquema tiver um namespace de destino não vazio:

- Outra janela do editor que contenha o esquema.

- Um esquema na solução atual.

- Um esquema do diretório de cache de esquema.

## <a name="xslt-files"></a>Arquivos XSLT
Ao editar um arquivo XSLT, o arquivo *XSLT. xsd* localizado no cache de esquema é usado para validação. Os erros de validação são mostrados como sublinhados ondulados azuis. Os erros do compilador XSLT são mostrados como sublinhados ondulados vermelhos.

## <a name="xml-schema-xsd-files"></a>Arquivos de esquema XML (XSD)
Ao editar um arquivo de esquema XML, o arquivo *xsdSchema. xsd* localizado no cache de esquema é usado para validação. Os erros de validação são mostrados como sublinhados ondulados azuis. Todos os erros de compilação também são mostrados com traços ondulados vermelhos.

## <a name="see-also"></a>Confira também

- [Editor de XML](../xml-tools/xml-editor.md)

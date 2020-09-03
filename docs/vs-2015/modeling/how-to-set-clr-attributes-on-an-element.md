---
title: 'Como: definir atributos CLR em um elemento | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72ad9175729451c82fca3b61d06e449edaf8cf38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662549"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Como definir atributos CLR em um elemento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Atributos personalizados são atributos especiais que podem ser adicionados a elementos de domínio, formas, conectores e diagramas. Você pode adicionar qualquer atributo que herda da `System.Attribute` classe.

### <a name="to-add-a-custom-attribute"></a>Para adicionar um atributo personalizado

1. No **Gerenciador de DSL**, selecione o elemento ao qual você deseja adicionar um atributo personalizado.

2. Na janela **Propriedades** , ao lado da propriedade **atributos personalizados** , clique no ícone procurar (**...**).

     A caixa de diálogo **Editar atributos** é aberta.

3. Na coluna **nome** , clique **\<add attribute>** e digite o nome do seu atributo. Pressione ENTER.

4. A linha abaixo do nome do atributo mostra parênteses. Nessa linha, digite um tipo de parâmetro para o atributo (por exemplo, `string` ) e pressione Enter.

5. Na coluna **propriedade de nome** , digite um nome apropriado, por exemplo, `MyString` .

6. Clique em **OK**.

     A propriedade **atributos personalizados** agora exibe o atributo no seguinte formato:

     `[`*AttributeName* `(` *ParameterName* `=` *Tipo* de`)]`

## <a name="see-also"></a>Consulte Também
 [Glossário das Ferramentas de Linguagem Específica de Domínio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)

---
title: Como definir atributos CLR em um elemento
description: Saiba como você pode adicionar qualquer atributo que herda da classe System. Attribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df9f8b16edcbe575ebac67f4acde9111a9511b85
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363842"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Como definir atributos CLR em um elemento
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

## <a name="see-also"></a>Veja também

- [Glossário das Ferramentas de Linguagem Específica de Domínio](/previous-versions/bb126564(v=vs.100))
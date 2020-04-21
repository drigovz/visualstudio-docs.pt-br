---
title: Elemento bandeira de comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84138a69dbb42fc349c12276fd7cca4b593e4d47
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649364"
---
# <a name="command-flag-eelement"></a>Bandeira de comando Eelement
Modifica seu elemento pai.

## <a name="syntax"></a>Sintaxe

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 A seção a seguir descreve valores de elemento válidos.

### <a name="attributes"></a>Atributos
 Nenhum.

### <a name="child-elements"></a>Elementos filho

|Valor|Descrição|
|-----------|-----------------|
|PermitirParams|Indica que os usuários podem inserir parâmetros de comando na janela **Comando** quando digitarem o nome canônico do comando.<br /><br /> Válido para:`Button`|
|Alwayscreate|O menu é criado mesmo que não tenha grupos ou botões.<br /><br /> Válido para:`Menu`|
|CaseSensitive|As entradas dos usuários são sensíveis a maiúsculas e minúsculas.<br /><br /> Válido para:`Combo`|
|CommandwellOnly|Aplique este sinalizador se o comando não aparecer no menu de nível superior e você quiser disponibilizá-lo para personalização adicional do shell, por exemplo, para vinculá-lo a um atalho de teclado. Depois que o VSPackage for instalado, você pode personalizar esses comandos abrindo a caixa de diálogo **Opções** e, em seguida, editando a colocação de comandos na categoria **Ambiente do Teclado.** Esse sinalizador não afeta a colocação em menus de atalho, barras de ferramentas, controladores de menu ou submenus.<br /><br /> Válido para: `Button`,`Combo`|
|PadrãoDesativado|Por padrão, o comando é desativado se o VSPackage que `QueryStatus` o implementa não estiver carregado ou o método não tiver sido chamado.<br /><br /> Válido para: `Button`,`Combo`|
|PadrãoDocked|Ancorado por padrão. Esta configuração não se aplica mais às barras de ferramentas porque elas estão sempre ancoradas.|
|PadrãoInvisível|Por padrão, o comando é invisível se o VSPackage que `QueryStatus` o implementa não estiver carregado ou o método não tiver sido chamado.<br /><br /> Recomendamos que você combine `DynamicVisibility` isso com a bandeira.<br /><br /> Válido `Button`para: `Combo`,`Menu`|
|DontCache|O ambiente de desenvolvimento `QueryStatus` não armazena os resultados do método para este comando.<br /><br /> Para um menu, isso diz a um controlador de menu para não armazenar o texto de seus itens de menu. Use este sinalizador quando o menu contiver itens dinâmicos ou itens que tenham texto dinâmico.<br /><br /> Válido para: `Button`,`Menu`|
|DynamicItemStart|Indica o início de uma lista dinâmica. Isso permite que o ambiente construa `QueryStatus` uma lista chamando sucessivamente o método de itens de lista até que a bandeira de OLECMDERR_E_UNSUPPORTED seja devolvida. Isso funciona bem para itens como listas de mru usadas mais recentemente e listas de janelas.<br /><br /> Válido para:`Button`|
|Visibilidade Dinâmica|A visibilidade do comando pode ser `QueryStatus` alterada através do método ou `VisibilityConstraints` através de um GUID de contexto incluído na seção.<br /><br /> Aplica-se a comandos que aparecem nos menus e nas barras de ferramentas da janela da ferramenta, mas não nas barras de ferramentas de nível superior que aparecem na janela principal. Os itens da barra de ferramentas de nível superior podem ser desativados, mas não ocultos, quando a bandeira OLECMDF_INVISIBLE é devolvida do `QueryStatus` método. Os comandos da barra de ferramentas que aparecem nas barras de ferramentas da janela da ferramenta podem ser ocultados.<br /><br /> Em um menu, este sinalizador também indica que ele deve ser automaticamente escondido quando todos os seus membros estão escondidos. Esse sinalizador é normalmente atribuído a submenus porque menus de nível superior já têm esse comportamento.<br /><br /> Esta bandeira deve ser `DefaultInvisible` combinada com a bandeira.<br /><br /> Válido `Button`para: `Combo`,`Menu`|
|Chaves de filtro|Consulte o tópico Teclas de filtragem em [Combo Element](../extensibility/combo-element.md).<br /><br /> Válido para:`Combo`|
|CorrigirMenuController|Se este comando estiver posicionado em um controlador de menu, o comando será sempre o padrão; ou seja, o comando é selecionado sempre que o próprio botão do controlador de menu é selecionado. Se o controlador `TextIsAnchorCommand` de menu tiver o conjunto de bandeiras, o `FixMenuController` controlador de menu também retirará seu texto do comando que tem o sinalizador.<br /><br /> Apenas um comando em um `FixMenuController` controlador de menu deve ter a bandeira. Se mais de um comando estiver tão marcado, o último comando no menu se tornará o comando padrão.<br /><br /> Válido para:`Button`|
|IconAndText|Mostrar um ícone e texto no menu e na barra de ferramentas.<br /><br /> Válido `Button`para: `Combo`,`Menu`|
|NoAutoComplete|O recurso de preenchimento automático está desativado.<br /><br /> Válido para:`Combo`|
|NoButtonPersonalizar|Não deixe que o usuário personalize este botão.<br /><br /> Válido para: `Button`,`Combo`|
|NoKeyCustomize|Não habilite a personalização do teclado.<br /><br /> Válido para: `Button`,`Combo`|
|NoshowOnMenucontroller|Se este comando estiver posicionado em um controlador de menu, o comando não aparecerá na lista suspensa.<br /><br /> Válido para:`Button`|
|NotInTBList|Não aparece na lista de barras de ferramentas disponíveis. Isso é válido apenas para os tipos de menu da Barra de Ferramentas.<br /><br /> Válido para:`Menu`|
|NoToolbarClose|O usuário não pode fechar a barra de ferramentas. Isso é válido apenas para os tipos de menu da Barra de Ferramentas.<br /><br /> Válido para:`Menu`|
|Pict|Mostrar apenas um ícone em uma barra de ferramentas, mas apenas texto em um menu. Se nenhum ícone for especificado, mostrará um espaço em branco clicável em uma barra de ferramentas.<br /><br /> Válido para:`Button`|
|Pós-Executivo|Faz com que o comando não bloqueie. O ambiente de desenvolvimento adia a execução até que todas as consultas de pré-processamento sejam concluídas.<br /><br /> Válido para:`Button`|
|RouteToDocs|O comando é encaminhado para o documento ativo.<br /><br /> Válido para:`Button`|
|AlongamentoHorizontalmente|Quando este sinalizador é definido, a largura se torna a largura mínima para a caixa de combinação, e se houver espaço na barra de ferramentas, a caixa de combinação se estende para preencher o espaço disponível. Isso só ocorre se a barra de ferramentas estiver encaixada horizontalmente, e apenas uma caixa de combinação na barra de ferramentas pode usar o sinalizador (o sinalizador é ignorado em todos, exceto na primeira caixa de combinação).<br /><br /> Válido para:`Combo`|
|Troca de texto|O texto de comando ou menu pode ser `QueryStatus` alterado em tempo de execução, normalmente através do método.<br /><br /> Válido para: `Button`,`Menu`|
|Texto''''''''''|Válido para:`Button`|
|Comando TextIsAnchor|Para um controlador de menu, o texto do menu é retirado do comando padrão (âncora). Um comando âncora é o último comando selecionado ou travado. Se este sinalizador não estiver definido, `MenuText` o controlador de menu usará seu próprio campo. No entanto, clicar no controlador de menu ainda habilita o último comando selecionado desse controlador.<br /><br /> Recomendamos que você combine `TextChanges` esta bandeira com a bandeira.<br /><br /> Este sinalizador se aplica apenas aos menus do tipo MenuController ou MenuControllerLatched.<br /><br /> Válido para:`Menu`|
|Menu textmenuCtrlUsemenu|Use `MenuText` o campo nos controladores de menu. O campo `ButtonText`padrão é .<br /><br /> Válido para:`Button`|
|TextMenuUseUseButton|Use `ButtonText` o campo para menus. O campo `MenuText` padrão é se for especificado.<br /><br /> Válido para:`Button`|
|Textonly|Mostrar apenas texto em uma barra de ferramentas ou em um menu, mas sem ícone, mesmo se o ícone estiver especificado.<br /><br /> Válido para:`Button`|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento botões](../extensibility/buttons-element.md)|Fornece um grupo para elementos [de botão.](../extensibility/button-element.md)|
|[Elemento menus](../extensibility/menus-element.md)|Define todos os menus que um VSPackage implementa.|

## <a name="see-also"></a>Confira também
- [Tabela de comando do Visual Studio (. Vsct) Arquivos](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

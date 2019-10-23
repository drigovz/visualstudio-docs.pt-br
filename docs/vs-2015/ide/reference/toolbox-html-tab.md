---
title: Caixa de ferramentas, Guia HTML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
ms.assetid: 9bfdd3b8-f5ac-4a5f-bdbf-c2b4e97641d8
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d3d6eafbafbf9b373028a7ba052ba9e8df62511c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661606"
---
# <a name="toolbox-html-tab"></a>Caixa de Ferramentas, Guia HTML
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A guia **HTML** da Caixa de ferramentas fornece componentes que são úteis em páginas e formulários da Web. Para exibir essa guia, primeiro abra um documento para edição no designer de HTML. No menu **Exibir**, clique em **Caixa de ferramentas** e, em seguida, na guia **HTML** da Caixa de ferramentas.

 Para criar uma instância de uma ferramenta na guia **HTML**, clique duas vezes na ferramenta para adicioná-la ao documento no ponto de inserção atual ou selecione a ferramenta e arraste-a para a posição desejada na superfície de edição.

## <a name="tasks"></a>Tarefas

- [Como gerenciar a janela Caixa de Ferramentas](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2)

- [Como manipular guias da caixa de ferramentas](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db)

## <a name="ui-elements"></a>Elementos da interface do usuário
 As ferramentas a seguir estão disponíveis por padrão na guia HTML.

 **Ponteiro** ![ASP.NET Mobile Designer HtmlPage](../../ide/reference/media/vxpointer.gif "|::ref1::|")

 Essa ferramenta é selecionada por padrão quando uma guia da Caixa de ferramentas é aberta. Não pode ser excluído. O ponteiro permite arrastar objetos para a superfície do modo de exibição de Design, redimensioná-los e reposicioná-los na página ou no formulário. Para obter mais informações, consulte [Como gerenciar a janela de ferramentas](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2) e [Como manipular as guias da caixa de ferramentas](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

 Botão **de entrada (botão)** ![página da Web HTML](../../ide/reference/media/vxbutton.gif "|::ref2::|")

 Insere um elemento `input` igual a `type="button"`. Para alterar o texto exibido, edite a propriedade `name`. Por padrão, `id="Button1"` é inserido para o primeiro botão, `id="Button2"` para o segundo e assim por diante.

 Ao arrastar **Entrada (Botão)** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:

```
<input id="Button1" type="button" value="Button" name="Button1">
```

 Para saber mais, veja [Controles de entrada HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Sintaxe declarativa do controle de servidor HtmlInputButton](https://msdn.microsoft.com/99ccf7fb-7e2a-4ba1-bcd9-981b619a16aa), [NIB: Como criar scripts e editar manipuladores de eventos](https://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [Mapa de conteúdo dos controles de servidor Web Button](https://msdn.microsoft.com/library/66b3ce28-3b93-4f0a-951f-42fb5bb5fddf), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, <xref:System.Web.UI.HtmlControls.HtmlButton> e <xref:System.Web.UI.WebControls.Button>.

 **Entrada (Redefinir)** ![captura de tela HTMLpageResetButton](../../ide/reference/media/vxreset.gif "|::ref3::|")

 Insere um elemento `input` igual a `type="reset"`. Para alterar o texto exibido, edite a propriedade `name`. Por padrão, `id="Reset1"` é inserido para o primeiro botão de redefinição, `id="Reset2"` para o segundo e assim por diante.

 Ao arrastar **Entrada (Redefinição)** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:

```
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

 Para saber mais, confira [Controles de entrada HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Sintaxe declarativa do controle de servidor HtmlInputReset](https://msdn.microsoft.com/cfc1f1fb-d33a-464d-9bb5-204e66174979), <xref:System.Web.UI.HtmlControls.HtmlInputButton> e <xref:System.Web.UI.WebControls.Button>.

 **Entrada (enviar)** ![captura de tela HTMLpageToolbarSubmitButton](../../ide/reference/media/vxsubmit.gif "|::ref4::|")

 Insere um elemento `input` igual a `type="submit"`. Para alterar o texto exibido, edite a propriedade `name`. Por padrão, `id="Submit1"` é inserido para o primeiro botão de envio, `id="Submit2"` para o segundo e assim por diante.

 Ao arrastar **Entrada (Envio)** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:

```
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

 Para saber mais, confira [Controles de entrada HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Sintaxe declarativa do controle de servidor HtmlInputSubmit](https://msdn.microsoft.com/eef2a157-f184-4ce9-b256-d1eacc7930f2), <xref:System.Web.UI.HtmlControls.HtmlInputButton> e <xref:System.Web.UI.WebControls.Button>.

 Captura **de tela de entrada (texto)** ![HTMLpageToolbarTextField](../../ide/reference/media/vxtextfield.gif "|::ref5::|")

 Insere um elemento `input` igual a `type="text"` no documento. Para alterar o texto padrão exibido, edite o atributo `value`. Por padrão, `id="Text1"` é inserido para o primeiro campo de texto, `id="Text2"` para o segundo e assim por diante.

 Ao arrastar **Entrada (Texto)** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:

```
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

 Para saber mais, confira [Controles de entrada HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Sintaxe declarativa do controle de servidor HtmlInputText](https://msdn.microsoft.com/87060d90-a11c-434d-9fc9-b03a8487041e), [Visão geral do controle de servidor Web TextBox](https://msdn.microsoft.com/library/ab354bc1-f23a-48fc-93d8-d4d7c1b7396f), <xref:System.Web.UI.HtmlControls.HtmlInputText> e <xref:System.Web.UI.WebControls.TextBox>.

> [!IMPORTANT]
> É recomendável validar todas as entradas do usuário. Para obter mais informações, consulte [Validando a entrada do usuário em Páginas da Web do ASP.NET](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 ![Campo de arquivo de página HTML](../../ide/reference/media/vxfilefield.gif "|::ref6::|") **de entrada (arquivo)**

 Insere um elemento `input` igual a `type="file"` no documento. Por padrão, `id="File1"` é inserido para o primeiro campo de arquivo, `id="File2"` para o segundo e assim por diante.

 Ao arrastar **Entrada (Arquivo)** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:

```
<input id="File1" type="file" name="File1">
```

 Para saber mais, confira [Controles de entrada HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Sintaxe declarativa do controle de servidor HtmlInputFile](https://msdn.microsoft.com/a817b4a0-056f-4c17-a696-b9fdcde43db6) e <xref:System.Web.UI.HtmlControls.HtmlInputFile>.

> [!IMPORTANT]
> É recomendável validar todas as entradas do usuário. Para obter mais informações, consulte [Validando a entrada do usuário em Páginas da Web do ASP.NET](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 Campo **de senha (senha) do** ![Visual Studio](../../ide/reference/media/vxpassword.gif "|::ref7::|") de entrada

 Insere um elemento `input` igual a `type="password"`. Por padrão, `id="Password1"` é inserido para o primeiro campo de senha, `id="Password2"` para o segundo e assim por diante.

 Ao arrastar **Entrada (Senha)** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:

```
<input id="Password1" type="password" name="Password1">
```

 Para obter mais informações, consulte [Controles de entrada HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Sintaxe declarativa do controle de servidor HtmlInputPassword](https://msdn.microsoft.com/df703dd0-1624-4e5a-a547-c97f2f331b9f), [Como definir um controle de servidor Web TextBox para uma entrada de senha](https://msdn.microsoft.com/library/5b5069f3-64a1-435a-aee6-da263f4e6310) e [Passo a passo: Validando uma entrada do usuário em uma página do Web Forms](https://msdn.microsoft.com/library/7141d6ba-34f3-410b-b5cd-2102a24cb436).

> [!IMPORTANT]
> Se o aplicativo transmitir nomes de usuário e senhas, será necessário configurar o site para usar o protocolo SSL para criptografar a transmissão. Para obter mais informações, consulte “Protegendo conexões com o protocolo SSL” no [Guia de Operações do IIS](http://go.microsoft.com/fwlink/?linkid=47856). Além disso, é recomendável validar todas as entradas do usuário. Para obter mais informações, consulte [Validando a entrada do usuário em Páginas da Web do ASP.NET](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 **Entrada (caixa de seleção) opção de caixa de** ![ferramentas da página da Web HTML](../../ide/reference/media/vxcheckbox.gif "|::ref8::|")

 Insere um elemento `input` igual a `type="checkbox"`. Para alterar o texto exibido, edite a propriedade `name`. Por padrão, `id="Checkbox1"` é inserido para a primeira caixa de seleção, `id="Checkbox2"` para a segunda e assim por diante.

 Ao arrastar **Entrada (Caixa de seleção)** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:

```
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

 Para saber mais, confira [Controles de entrada HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Sintaxe declarativa do controle de servidor HtmlInputCheckBox](https://msdn.microsoft.com/4a509586-89d8-4ccf-a0b8-b9160ce6e4a6), [Visão geral dos controles de servidor Web CheckBox e CheckBoxList](https://msdn.microsoft.com/library/3028dfd3-e2c5-451d-9150-d02c8ffb92bf), <xref:System.Web.UI.HtmlControls.HtmlInputCheckBox> e <xref:System.Web.UI.WebControls.CheckBox>.

 Captura **de tela de entrada (rádio)** ![VisualStudioHTMLpageRadioButton](../../ide/reference/media/vxradio.gif "|::ref9::|")

 Insere um elemento `input` igual a `type="radio"`. Para alterar o texto exibido, edite a propriedade `name`. Por padrão, `id="Radio1"` é inserido para o primeiro botão de opção, `id="Radio2"` para o segundo e assim por diante.

 Ao arrastar **Entrada (Botão de opção)** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:

```
<input id="Radio1" type="radio" name="Radio1">
```

 Para saber mais, confira [Controles de entrada HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Sintaxe declarativa do controle de servidor HtmlInputRadioButton](https://msdn.microsoft.com/6e60ff63-cc57-46ef-bf96-e829e204ba33), [Visão geral dos controles de servidor Web RadioButton e RadioButtonList](https://msdn.microsoft.com/library/20eb383c-4b59-432b-bba3-e9d785107747), <xref:System.Web.UI.HtmlControls.HtmlInputRadioButton> e <xref:System.Web.UI.WebControls.RadioButton>.

 ![Item oculto da página HTML](../../ide/reference/media/vxhidden.gif "|::ref10::|") **de entrada (oculto)**

 Insere um elemento `input` igual a `type="hidden"`. Por padrão, `id="Hidden1"` é inserido para o primeiro campo oculto, `id="Hidden2"` para o segundo e assim por diante.

 Ao arrastar **Entrada (Oculta)** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:

```
<input id="Hidden1" type="hidden" name="Hidden1">
```

 Para saber mais, confira [Controles de entrada HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Sintaxe declarativa do controle de servidor HtmlInputHidden](https://msdn.microsoft.com/4194e44d-1d74-4bfc-9cc7-743a2e1ea5f9) e <xref:System.Web.UI.HtmlControls.HtmlInputHidden>.

 ![Área de texto da barra de ferramentas HtmlPage](../../ide/reference/media/vxtextarea.gif "|::ref11::|") **TextArea**

 Insere um elemento `textarea`. É possível redimensionar a área de texto ou usar as barras de rolagem para exibir o texto que se estende além da área de exibição. Para alterar o texto padrão exibido, edite o atributo `value`. Por padrão, `id="textarea1"` é inserido para a primeira área de texto, `id=" textarea 2"` para a segunda e assim por diante.

 Ao arrastar **Área de texto** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:

```
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

 Para saber mais, confira [Sintaxe declarativa do controle de servidor HtmlTextArea](https://msdn.microsoft.com/5a103ffa-235b-4452-ba2b-a4fb8ba8cb87), <xref:System.Web.UI.HtmlControls.HtmlTextArea> e <xref:System.Web.UI.WebControls.TextBox>.

> [!IMPORTANT]
> É recomendável validar todas as entradas do usuário. Para obter mais informações, consulte [Validando a entrada do usuário em Páginas da Web do ASP.NET](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 Captura de tela de **tabela** ![HTMLpageToolbarTable](../../ide/reference/media/vxtable.gif "|::ref12::|")

 Insere um elemento `table`.

 Ao arrastar **Tabela** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:

```
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

 Para saber mais, confira [Sintaxe declarativa do controle de servidor HtmlTable](https://msdn.microsoft.com/625b06d8-0f69-4112-a1d4-8ef2a9fbcda9), [Visão geral dos controles de servidor Web Table, TableRow e TableCell](https://msdn.microsoft.com/library/2fbd0582-cf69-4c8d-9e35-21f35e2cee1a), <xref:System.Web.UI.HtmlControls.HtmlTable> e <xref:System.Web.UI.WebControls.Table>.

 ![Item de imagem da página HTML da](../../ide/reference/media/vximage.gif "|::ref13::|") **imagem**

 Insere um elemento `img`. Edite esse elemento para especificar seu `src` e seu texto `alt`.

 Ao arrastar **Imagem** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:

```
<img alt="" src="">
```

 Para saber mais, confira [Sintaxe declarativa do controle de servidor HtmlImage](https://msdn.microsoft.com/528430e8-ced1-47d1-8db2-942e734a61f6), [Visão geral do controle de servidor Image](https://msdn.microsoft.com/library/096a8d8d-58ee-4ee8-ab82-6594a0f3a0a9), <xref:System.Web.UI.HtmlControls.HtmlImage>, <xref:System.Web.UI.HtmlControls.HtmlInputImage> e <xref:System.Web.UI.WebControls.Image>.

 **Selecionar** ![menu suspenso caixa de ferramentas de página HTML](../../ide/reference/media/vxdropdown.gif "|::ref14::|")

 Insere um elemento `select` suspenso (sem um atributo `size`). Por padrão, `id="select1"` é inserido para a primeira caixa de listagem, `id="select2"` para a segunda e assim por diante.

 Ao arrastar **Selecionar** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:

```
<select id="select1" name="select1"><option selected></option></select>
```

 É possível criar um elemento `select` multilinha aumentando o valor da propriedade de tamanho.

 Para saber mais, confira [Sintaxe declarativa do controle de servidor HtmlSelect](https://msdn.microsoft.com/ee93bdec-b343-441a-a8ff-56ffcafe9ae5), [NIB: Como criar scripts e editar manipuladores de eventos](https://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [Visão geral do controle de servidor Web DropDownList](https://msdn.microsoft.com/library/517dd1a4-8df3-4c9f-8c89-1549a1aee608), [Visão geral do controle de servidor Web ListBox](https://msdn.microsoft.com/library/c08ee025-787a-408d-858e-a4a5fdb61d97), <xref:System.Web.UI.HtmlControls.HtmlSelect> e <xref:System.Web.UI.WebControls.DropDownList>.

 ![Item de regra horizontal da página HTML da](../../ide/reference/media/vxhorizontal.gif "|::ref15::|") **regra horizontal**

 Insere um elemento `hr`. Para aumentar a espessura da linha, edite o atributo `size`.

 Ao arrastar **Régua Horizontal** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:

```
<hr width="100%" size=1>
```

 Para obter mais informações, consulte [Controle HTML Regra Horizontal](https://msdn.microsoft.com/library/bf6df0a8-9844-404d-8a9a-3455b0180f2f).

 ![Rótulo de página HTML](../../ide/reference/media/vxlabel.gif "|::ref16::|") de **div**

 Insere um elemento `div` inclui um atributo `ms_positioning="FlowLayout"`. Com exceção da largura e da altura, esse item é idêntico a um Painel de Layout de Fluxo. Para formatar o texto contido em um elemento `div`, adicione um atributo `class="stylename"` à marcação de abertura.

 Ao arrastar **Div** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:

```
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

 Para saber mais, confira [Controle HTML Div](https://msdn.microsoft.com/library/585fa702-4408-4af1-a92b-68d77ee5e995), [Visão geral do controle de servidor Web Label](https://msdn.microsoft.com/library/990558d1-4b22-4f28-b100-78a434b3c5ac) e <xref:System.Web.UI.WebControls.Label>.

## <a name="see-also"></a>Veja também
 Guia padrão da [caixa de ferramentas](../../ide/reference/toolbox.md) , [controles HTML](https://msdn.microsoft.com/library/83bc6f7e-a2b5-4fe9-9a34-eb34aef673be) da [caixa de ferramentas](https://msdn.microsoft.com/library/35e9320d-fcbd-474b-8b8f-55705e9a1870)

---
title: Microsoft Help Viewer SDK | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 721623edabcaf3b395a143dd193cae3fd71d93d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707149"
---
# <a name="microsoft-help-viewer-sdk"></a>SDK do Microsoft Help Viewer

Este artigo contém as seguintes tarefas para integradores visual studio help viewer:

- Criando um tópico (suporte à F1)

- Criando um pacote de marca de conteúdo do Help Viewer

- Implantação de um conjunto de artigos

- Adicionando ajuda ao shell do Visual Studio (integrado ou isolado)

- Recursos adicionais

## <a name="create-a-topic-f1-support"></a>Criar um tópico (suporte à F1)

Esta seção fornece uma visão geral dos componentes de um tópico apresentado, requisitos de tópicos, uma breve descrição de como criar um tópico (incluindo requisitos de suporte à F1) e, finalmente, um tópico de exemplo com seu resultado renderizado.

**Visão geral do tópico do visualizador de ajuda**

Quando um tópico é chamado para renderização, o Help Viewer obtém os elementos do pacote de marca que estão associados ao tópico no momento da instalação ou última atualização, juntamente com o tópico XHTML, e combina os dois para resultar na visualização de conteúdo apresentada (dados de marca + dados de tópico).  O pacote de marca contém logotipos, suporte para comportamentos de conteúdo e texto de marca (direitos autorais, etc.).  Consulte "Criando pacote de marca" abaixo para obter mais informações sobre os elementos do pacote de marca.  Caso não haja um pacote de marca associado ao tópico, o Help Viewer usará o pacote de marca de retorno localizado na raiz do aplicativo Help Viewer (Branding_en-EUA.mshc).

**Ajude os requisitos do tópico do visualizador**

Para ser renderizado corretamente dentro do Help Viewer, o conteúdo do tópico bruto deve ser W3C Basic 1.1 XHTML.

Um tópico normalmente contém duas seções:

- Metadados (ver Referência de Metadados de Conteúdo): dados sobre o tópico, por exemplo, o tópico ID exclusivo, valor de palavra-chave, o tópico TOC ID, ID de nó pai, etc.

- Conteúdo do corpo: compatível com o W3C Basic 1.1 XHTML, que inclui comportamentos de conteúdo suportados (área dobrável, trecho de código, etc. A lista completa é mostrada abaixo).

Controles suportados pelo Visual Studio Branding Package:

- Links

- Codesnippet

- Área dobrável

- Membro Herdado

- Texto específico do idioma

Cordas de linguagem suportadas (não sensíveis a maiúsculas e minúsculas):

- javascript

- csharp ou c #

- cplusplus ou visualc++ ou c++

- jscript

- visualbasic ou vb

- f# ou fsharp ou fs

- outro - uma string que representa um nome de linguagem

**Criando um tópico do Visualizador de Ajuda**

Crie um novo documento XHTML chamado ContosoTopic4.htm e inclua a tag título (abaixo).

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

Em seguida, adicione dados para definir como o tópico deve ser apresentado (auto-marcado ou não), como referenciar este tópico para F1, onde este tópico existe dentro do TOC, seu ID (para referência de link por outros tópicos), etc. Consulte a tabela "Metadados de conteúdo" abaixo para obter uma lista completa de metadados suportados.

- Neste caso, usaremos nosso próprio pacote de marca, uma variante do pacote de marca Visual Studio Help Viewer.

- Adicione o nome e o valor do meta F1 ("Microsoft.Help.F1" content=" ContosoTopic4") que corresponderá ao valor de F1 fornecido na bolsa de propriedade IDE. (Consulte a seção de suporte da F1 para obter mais informações.) Este é o valor que é compatível com a chamada de F1 de dentro do IDE para exibir este tópico quando a F1 é escolhida no IDE.

- Adicione o iD de tópico. Esta é a string que é usada por outros tópicos para vincular a este tópico. É o ID do Visualizador de Ajuda para este tópico.

- Para o TOC, adicione o nó pai deste tópico para definir onde este tópico do nó TOC será exibido.

- Para o TOC, adicione a ordem de nó deste tópico. Quando o nó `n` pai tiver número de nódulos para filhos, defina na ordem dos nódulos da criança a localização deste tópico. Por exemplo, este tópico é o número 4 de 4 tópicos infantis.

Seção de metadados por exemplo:

```html
<html>
<head>
<title>Contoso Topic 4</title>

<meta name="SelfBranded" content="false" />
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />

</head>

<body>

</body>
</html>
```

**O Corpo Tópico**

O corpo (sem incluir o cabeçalho e o rodapé) do tópico conterá links de página, uma seção de notas, uma área dobrável, um trecho de código e uma seção de texto específico do idioma.  Consulte a seção de branding para obter informações sobre as áreas do tópico apresentado.

1. Adicionar uma tag de título tópico:`<div class="title">Contoso Topic 4</div>`

2. Adicione uma seção de notas:`<div class="alert"> add your table tag and text </div>`

3. Adicione uma área dobrável:`<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. Adicionar um trecho de código:`<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. Adicionar texto específico para `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` linguagem `devLangnu=` de código: Nota que permite que você insira outros idiomas. Por exemplo, `devLangnu="Fortran"` exibe Fortran quando o trecho de código DisplayLanguage = Fortran

6. Adicionar links de página:`<a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> Nota: para a nova coloração de código "Display Language" (exemplo, F#, Cobol, Fortran) a coloração do código no trecho de código será monocromática.

**Exemplo de ajuda ao tópico do visualizador** O código ilustra como definir metadados, um trecho de código, uma área dobrável e texto específico do idioma.

```html
<?xml version="1.0" encoding="utf-8"?>
<html>
<head>
<title>Contoso Topic 4</title>

    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />
<meta name="SelfBranded" content="false" />
</head>

<body>
<div class="title">Contoso Topic 4</div>

  <div id="header">
<table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%">
        <tr id="headerTableRow2"><td align="left">
            <span id="nsrTitle">Contoso Topic 1</span>
          </td>
<td align="right">
</td></tr>
<tr id="headerTableRow1"><td align="left">
            <span id="runningHeaderText">Contoso Widgets & Sprockets</span>
          </td></tr>
      </table>
</div>

<h2>Table of Contents</h2>

<ul class="toc">
<li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li>
<li class="tocline1"><a href="#seealso" target="_self">See Also</a></li>
</ul>

<div class="topic">

<div id="mainSection">
<div id="mainBody">

<a name="introduction"></a>
<h2>1.0 Introduction</h2>
<p>[This documentation is for sample purposes only.]</p>

<p>Contoso Topic 1 contains examples of:
<ul>
<li>Collapsible Area</li>
<li>Bookmark ("See also")</li>
<li>Code Snippets from Branding Package</li>
</ul>
 </p>
<div class="alert"><table><tr><th>
<strong>Note </strong></th></tr>
<tr><td>
<p>This is an example of a <span class="label">Note </span>section.
Call out important items for your reader in this <span class="label">Note </span>box.
</p></td></tr>
</table>
</div>
</div>

<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading">

            <a id="sectionToggle0"><!----></a>

<div>
Example of Collapsible Area
<br/>
Lorem ipsum dolor sit amet...
</div>
</CollapsibleArea>

<div id="snippetGroup" >
<CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" >
Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip
Dim messageBoxVB as New System.Text.StringBuilder()
    messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds)
    messageBoxVB.AppendLine()
 ...
    MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event")
End Sub
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" >
private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e)
{
System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder();
messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds );
messageBoxCS.AppendLine();
...
MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" );
}
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" >
some F# code
</CodeSnippet>
</div>

<h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />

<a name="seealso"></a>
<h1 class="heading">See Also</h1>

    <div id="seeAlsoSection" class="section">
    <div class="seeAlsoStyle">
        <a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>
    </div>
 </div>
</div>
</div>
</body>
</html>
```

**Suporte à F1**

No Visual Studio, a seleção do F1 gera valores fornecidos a partir da colocação do cursor dentro do IDE e preenche um "saco de propriedade" com os valores fornecidos (com base na localização do cursor. Quando o cursor está sobre o recurso x, o recurso x está ativo/em foco e preenche o saco de propriedade com valores.  Quando o F1 é selecionado, o saco de propriedade é preenchido e o código Visual Studio F1 procura ver se a fonte de ajuda padrão dos clientes é local ou on-line (on-line é o padrão), em seguida, cria a seqüência apropriada com base na configuração dos usuários (on-line é o padrão) - shell execute (consulte o Guia de Administrador de Ajuda para parâmetros de lançamento exe) com parâmetros para o visualizador de ajuda local + palavra-chave(s) do saco de propriedade se a ajuda local for o padrão , ou a URL MSDN com a palavra-chave na lista de parâmetros.

Se três strings forem devolvidas para a F1, referida como uma seqüência de vários valores, pegue o primeiro termo, procure um hit e, se encontrado, estamos prontos; se não, mova-se para a próxima string.  A ordem importa. A apresentação das palavras-chave de vários valores deve ser a seqüência de string mais longa para a seqüência mais curta.  Para verificar isso no caso de palavras-chave de vários valores, consulte a seqüência de URL online f1, que incluirá a palavra-chave escolhida.

No Visual Studio 2012, intencionalmente fizemos uma divisão mais forte entre on-line e off-line, de modo que se a configuração do usuário fosse para Online, então simplesmente passamos a solicitação de F1 diretamente para o nosso serviço de consulta on-line no MSDN em vez de roteamento através do Help Library Agent que tínhamos no Visual Studio 2010. Em seguida, contamos com um estado de "conteúdo do fornecedor instalado = verdadeiro" para determinar se devemos fazer algo diferente nesse contexto. Se for verdade, executamos essa lógica de análise e roteamento, dependendo do que você deseja apoiar para seus clientes. Se for falso, então vamos ao MSDN. Se a configuração do usuário for para Local, então todas as chamadas vão para o mecanismo de ajuda local.

Diagrama de fluxo de F1:

![Fluxo de F1](../../extensibility/internals/media/f1flow.png "F1flow")

Quando a fonte de conteúdo de ajuda padrão do Help Viewer é definida como on-line (Lançamento no navegador):

- Visual Studio Partner (VSP) apresenta a eitação de um valor para a bolsa de propriedade F1 (prefixo de bolsa de propriedade e URL on-line para o prefixo encontrado no registro): F1 envia um vsp parâmetros URL+ para o navegador.

- Recursos do Visual Studio (editor de idiomas, itens de menu específicos do Visual Studio, etc.): O F1 envia uma URL do Visual Studio para o navegador.

Quando a fonte de conteúdo de ajuda padrão do Help Viewer for definida como Ajuda local (Iniciar no Visualizador de Ajuda):

- VSP apresenta onde a palavra-chave corresponde entre o saco de propriedade F1 e o índice da loja local (ou seja, a palavra-chave do saco de propriedade = o valor encontrado no índice da loja local): F1 renderiza o tópico no Visualizador de Ajuda.

- Recursos do Visual Studio (nenhuma opção para o VSP substituir a bolsa de propriedade emitida a partir de recursos do Visual Studio): o F1 renderiza um tópico do Visual Studio no Help Viewer.

Defina os seguintes valores de registro para ativar o retorno do F1 para o conteúdo da Ajuda do fornecedor. O F1 Fallback significa que o Help Viewer está definido para procurar conteúdo de Ajuda de F1 on-line, e o conteúdo do fornecedor é instalado localmente no disco rígido dos usuários. O Visualizador de Ajuda deve olhar para a ajuda local para o conteúdo, mesmo que a configuração padrão seja para ajuda on-line.

1. Defina o valor **vendorContent** sob a chave de registro Ajuda 2.3:

   - Para sistemas operacionais de 32 bits:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent"=dword:00000001

   - Para sistemas operacionais de 64 bits:

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catálogos\VisualStudio15

        "VendorContent"=dword:00000001

2. Registre o namespace do parceiro sob a chave de registro Ajuda 2.3:

   - Para sistemas operacionais de 32 bits:

      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Espaço<em> \\ de nome do<do parceiro\></em>

      "localização"="offline"

   - Para sistemas operacionais de 64 bits:

      HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Espaço<em> \\ de nome<do parceiro\></em>

      "localização"="offline"

**Análise de namespace nativo da base**

Para ativar o parsing de namespace nativo base, no registro adicione um novo DWORD com o nome de: BaseNativeNamespaces e defina seu valor como 1 (sob a tecla de catálogo que eles desejam suportar).  Por exemplo, se você quiser usar o catálogo do Visual Studio, você pode adicionar a chave ao caminho:

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catálogos\VisualStudio15

Quando uma palavra-chave F1 no formato CABEÇALHO/MÉTODO for encontrada, o caractere '/' será analisado, resultando na seguinte construção:

- CABEÇALHO: será o namespace que pode ser usado para registrar no registro

- MÉTODO: esta será a palavra-chave que passa.

Por exemplo, dada uma biblioteca personalizada chamada CustomLibrary e um método chamado MyTestMethod, `CustomLibrary/MyTestMethod`quando uma solicitação de F1 chegar nele será formatado como .

Um usuário pode então registrar customLibrary como o namespace sob a colmeia Parceiros e fornecer qualquer chave de localização que desejar, e a palavra-chave passada para a consulta será MyTestMethod.

**Habilitar a ferramenta de depuração de ajuda no IDE**

Adicione a seguinte chave de registro e valor:

::: moniker range="vs-2017"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Ajuda dinâmica**

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Ajuda dinâmica**

::: moniker-end

Valor: Saída de depuração de exibição em dados de varejo: SIM

No IDE, no item 'Ajuda' do menu Ajuda, selecione **'Depurar', 'Depurar'.**

**Metadados de conteúdo**

Na tabela a seguir, qualquer string que apareça entre os suportes é um espaço reservado que deve ser substituído por um valor reconhecido. Por exemplo, \<em meta name="Microsoft.Help.Locale" conteúdo="[código de idioma]" />, "[código de idioma]" deve ser substituído por um valor como "en-us".

| Propriedade (Representação HTML) | Descrição |
| - | - |
| \<meta name="Microsoft.Help.Locale" conteúdo="[código de idioma]" /> | Define um local para este tópico. Se esta tag for usada em um tópico, ela deve ser usada apenas uma vez e deve ser inserida acima de qualquer outra tag Microsoft Help. Se esta tag não for usada, o texto do corpo do tópico será indexado usando o disjuntor de palavras associado à localização do produto, se for especificado; caso contrário, o disjuntor de palavras en-us é usado. Esta tag está em conformidade com isoc RFC 4646. Para garantir que o Microsoft Help funcione corretamente, use essa propriedade em vez do atributo lingual geral. |
| \<meta name="Microsoft.Help.TopicLocale" conteúdo="[código de idioma]" /> | Define um local para este tópico quando outros locais também são usados. Se esta tag for usada em um tópico, ela deve ser usada apenas uma vez. Use esta tag quando o catálogo contiver conteúdo em mais de um idioma. Vários tópicos em um catálogo podem ter o mesmo ID, mas cada um deve especificar um TopicLocale exclusivo. O tópico que especifica um TopicLocale que corresponde ao local do catálogo é o tópico exibido na tabela de conteúdos. No entanto, todas as versões de idioma do tópico são exibidas nos resultados da Pesquisa. |
| \<título>[Título]\</> de título | Especifica o título deste tópico. Esta tag é necessária e deve ser usada apenas uma vez em um tópico. Se o corpo do tópico não \<contiver uma seção de div> título, este Título será exibido no tópico e na tabela de conteúdos. |
| \<meta name=" Microsoft.Help.Keywords" content="[aKeywordPhrase]"/> | Especifica o texto de um link exibido no painel de índice do Visualizador de ajuda. Quando o link é clicado, o tópico é exibido. Você pode especificar várias palavras-chave de índice para um tópico, ou pode omitir essa tag se não quiser que links para este tópico apareçam no índice. Palavras-chave "K" de versões anteriores do Help podem ser convertidas nesta propriedade. |
| \<meta name="Microsoft.Help.Id" conteúdo="[TopicID]"/> | Define o identificador para este tópico. Esta tag é necessária e deve ser usada apenas uma vez em um tópico. O ID deve ser único entre os tópicos do catálogo que possuem a mesma configuração local. Em outro tópico, você pode criar um link para este tópico usando este ID. |
| \<meta name="Microsoft.Help.F1" conteúdo="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/> | Especifica a palavra-chave F1 para este tópico. Você pode especificar várias palavras-chave f1 para um tópico, ou pode omitir esta tag se não quiser que este tópico seja exibido quando um usuário do aplicativo pressiona F1. Normalmente, apenas uma palavra-chave f1 é especificada para um tópico. Palavras-chave "F" de versões anteriores do Help podem ser convertidas nesta propriedade. |
| \<meta name="Description" content="[descrição do tópico]" /> | Fornece um breve resumo do conteúdo neste tópico. Se esta tag for usada em um tópico, ela deve ser usada apenas uma vez. Esta propriedade é acessada diretamente pela biblioteca de consulta; ele não está armazenado no arquivo de índice. |
| meta name="Microsoft.Help.TocParent" conteúdo="[parent_Id]"/> | Especifica o tópico pai deste tópico na tabela de conteúdo. Esta tag é necessária e deve ser usada apenas uma vez em um tópico. O valor é a Microsoft.Help.Id dos pais. Um tópico pode ter apenas um local na tabela de conteúdo. "-1" é considerado o tópico ID para a raiz TOC. Em [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)], essa página é a página inicial do Help Viewer. Esta é a mesma razão pela qual adicionamos especificamente TocParent=-1 a alguns tópicos para garantir que eles apareçam no nível superior. A página inicial do Help Viewer é uma página do sistema e, portanto, não substituível. Se um VSP tentar adicionar uma página com um ID de -1, ele pode ser adicionado ao conjunto de conteúdo, mas o Help Viewer sempre usará a página do sistema - Help Viewer Home |
| \<meta name="Microsoft.Help.TocOrder" conteúdo="[inteiro positivo]"/> | Especifica onde na tabela de conteúdo este tópico aparece em relação aos seus tópicos de pares. Esta tag é necessária e deve ser usada apenas uma vez em um tópico. O valor é um inteiro. Um tópico que especifica um inteiro de menor valor aparece acima de um tópico que especifica um inteiro de maior valor. |
| \<meta name="Microsoft.Help.Product" conteúdo="[código do produto]"/> | Especifica o produto que este tópico descreve. Se esta tag for usada em um tópico, ela deve ser usada apenas uma vez. Essas informações também podem ser fornecidas como um parâmetro que é passado para o Índice de Ajuda. |
| \<meta name="Microsoft.Help.ProductVersion" conteúdo="[número da versão]"/> | Especifica a versão do produto que este tópico descreve. Se esta tag for usada em um tópico, ela deve ser usada apenas uma vez. Essas informações também podem ser fornecidas como um parâmetro que é passado para o Índice de Ajuda. |
| \<meta name="Microsoft.Help.Category" conteúdo="[string]"/> | Usado por produtos para identificar subseções de conteúdo. Você pode identificar várias subseções para um tópico ou pode omitir essa tag se não quiser que os links identifiquem quaisquer subseções. Esta tag é usada para armazenar os atributos para TargetOS e TargetFrameworkMoniker quando um tópico é convertido de uma versão anterior do Help. O formato do conteúdo é AttributeName:AttributeValue. |
| \<meta name="Microsoft.Help.TopicVersion content="[topic version number]"/> | Especifica esta versão do tópico quando várias versões existem em um catálogo. Como Microsoft.Help.Id não é garantido ser único, essa tag é necessária quando mais de uma versão de um tópico existe em um catálogo, por exemplo, quando um catálogo contém um tópico para o .NET Framework 3.5 e um tópico para o .NET Framework 4 e ambos têm o mesmo Microsoft.Help.Id. |
| \<meta name="SelfBranded" content="[TRUE ou FALSE]"/> | Especifica se esse tópico usa o pacote de marca inicial do Help Library Manager ou um pacote de marca específico para o tópico. Esta tag deve ser VERDADEIRA ou FALSA. Se for TRUE, então o pacote de marca para o tópico associado substitui o pacote de marca definido quando o Help Library Manager começa para que o tópico seja renderizado como pretendido, mesmo que difere da renderização de outros conteúdos. Se for FALSE, o tópico atual será renderizado de acordo com o pacote de marca definido quando o Help Library Manager é iniciado. Por padrão, o Help Library Manager assume que a auto-marca é falsa, a menos que a variável SelfBranded seja declarada COMO TRUE; portanto, você não precisa \<declarar meta name="SelfBranded" conteúdo="FALSO"/>. |

## <a name="create-a-branding-package"></a>Crie um pacote de marca

O lançamento do Visual Studio abrange uma série de diferentes produtos do Visual Studio, incluindo as conchas isoladas e integradas para os Parceiros do Visual Studio.  Cada um desses produtos requer algum grau de suporte de marca de conteúdo de ajuda baseado em tópicos, exclusivo para o produto.  Por exemplo, os tópicos do Visual Studio precisam ter uma apresentação consistente da marca, enquanto o SQL Studio, que envolve a ISO Shell, requer sua própria marca de conteúdo de Ajuda exclusiva para cada tópico.  Um parceiro shell integrado pode querer que seus tópicos de Ajuda estejam dentro do conteúdo de ajuda do produto Visual Studio pai, mantendo sua própria marca de tópicos.

Os pacotes de marca são instalados pelo produto que contém o Visualizador de Ajuda.  Para produtos do Visual Studio:

- Um pacote de marca\<de recuo (Branding_ locale>.mshc) está instalado na raiz do aplicativo Help Viewer 2.3 (exemplo: C:\Arquivos de programa (x86)\Microsoft Help Viewer\v2.3) pelo pacote de idiomas Help Viewer.  Isso é usado para casos em que o pacote de marca do produto não está instalado (nenhum conteúdo foi instalado) ou onde o pacote de marca instalado está corrompido.  Os elementos do Visual Studio (logotipo e Feedback) são ignorados quando o pacote de marca de recuo raiz do aplicativo é usado.

- Quando o conteúdo do Visual Studio é instalado a partir do serviço de pacotede conteúdo, um pacote de marca também é instalado (pela primeira vez cenário de instalação de conteúdo).  Se houver uma atualização no pacote de marca, a atualização será instalada quando a próxima atualização de conteúdo ou ação adicional de instalação do pacote acontecer.

O Microsoft Help Viewer suporta a marca de tópicos com base em metadados de tópicos.

- Quando os metadados tópicos definem auto-marca = verdadeiro, torne o tópico como está, não faça nada (na medida em que a marca).

- Quando os metadados de tópicos definirem auto-marca = falso, use o pacote de marca associado ao valor de metadados do TopicVendor.

- Quando os metadados de tópico definem o nome="Microsoft.Help.TopicVendor" conteúdo=\< nome do pacote de marca no fornecedor MSHA>, use o pacote de marca definido no valor de conteúdo.

- Dentro do catálogo do Visual Studio, há uma aplicação prioritária de Pacotes de Marca.  Primeiro a marca padrão do Visual Studio é aplicada e, em seguida, se definida nos metadados tópicos e suportada com o pacote de marca associado (conforme definido no msha de instalação), a marca definida pelo fornecedor é aplicada como uma substituição.

Os elementos de marca geralmente se enquadram em três categorias principais:

- Elementos de cabeçalho (exemplos incluem link de feedback, texto de isenção de responsabilidade condicional, logotipo)

- Comportamentos de conteúdo (exemplos incluem elementos de texto de controle de expansão/colapso e elementos de trecho de código)

- Elementos de rodapé (exemplo Direitos Autorais)

Itens considerados como elementos de marca incluem (detalhados nesta especificação):

- Logotipo de catálogo/produto (exemplo, Visual Studio)

- Link de feedback e elementos de e-mail

- Texto de isenção de responsabilidade

- Texto de direitos autorais

Os arquivos de suporte no pacote de marca Visual Studio Help Viewer incluem:

- Gráficos (logotipos, ícones, etc.)

- Branding.js - arquivos de script que suportam comportamentos de conteúdo

- Branding.xml - strings que são consistentemente usadas em todo o conteúdo do catálogo.  Nota: para os elementos de texto de localização do\<Visual Studio no branding.xml, inclua _locID=" valor único>"

- Branding.css - definições de estilo para consistência de apresentação

- Printing.css - definições de estilo para apresentação impressa consistente

Como observado acima, os Pacotes de Marca estão associados ao tópico:

- Quando selfBranded = false é definido nos metadados, o tópico herda o pacote de marca de catálogo

- Ou quando selfBranded = false e há um pacote de marca exclusivo definido no MSHA e disponível quando o conteúdo é instalado

Para VSPs que implementam pacotes de marca personalizados (conteúdo VSP, SelfBranded=True), uma maneira de proceder é começar com o pacote de marca de recuo (instalado com o Help Viewer) e alterar o nome do arquivo conforme apropriado.  O\<Branding_ arquivo locale>.mshc é um arquivo zip com a extensão do arquivo alterada para .mshc, então basta alterar a extensão de .mshc para .zip e extrair o conteúdo.  Veja abaixo os elementos do pacote de marca e modifique conforme apropriado (por exemplo, altere o logotipo para o logotipo VSP e a referência ao logotipo no arquivo Branding.xml, atualize Branding.xml por especificações VSP, etc.).

Quando todas as modificações forem feitas, crie um arquivo zip contendo os elementos de marca desejados e altere a extensão para .mshc.

Para associar o pacote de marca personalizado, crie o MSHA, que contém a referência ao arquivo mshc da marca junto com o conteúdo mshc (contendo os tópicos).  Veja abaixo "MSHA" para saber como criar um MSHA básico.

O arquivo Branding.xml contém uma lista de elementos usados para renderizar \<consistentemente itens específicos em um tópico quando o tópico contém meta name="Microsoft.Help.SelfBranded" conteúdo="falso"/>.  A lista visual studio de elementos no arquivo Branding.xml está listada abaixo.  Esta lista destina-se a ser usada como um modelo para os adotantes da ISO Shell, onde eles modificam esses elementos (por exemplo, logotipo, feedback e direitos autorais) para atender às suas próprias necessidades de marca de produtos.

Nota: variáveis observadas por "{n}" têm dependências de código - remover ou alterar esses valores causará erros e possivelmente falha de aplicativo. Os identificadores de localização (exemplo _locID="codesnippet.n") estão incluídos no Visual Studio Branding Package.

**Branding.xml**

| | |
| - | - |
| Recurso: | **Área dobrável** |
| Use: | Expandir colapsa texto de controle de conteúdo |
| **Elemento** | **Valor** |
| Expandirtexto | Expanda |
| ColapsoText | Recolher |
| Recurso: | **Codesnippet** |
| Use: | Texto de controle de trecho de código.  Nota: O conteúdo do trecho de código com espaço "Não-Quebra" será alterado para o espaço. |
| **Elemento** | **Valor** |
| Copytoclipboard | Copiar para a Área de Transferência |
| VerTexto colorido | Ver Colorido |
| CombinadoVBTabDisplayLanguage | Visual Basic (Amostra) |
| VBDeclaração | Declaração |
| VBUsage | Uso |
| Recurso: | **Feedback, Rodapé e Logotipo** |
| Use: | Forneça um controle de feedback para que o cliente forneça feedback sobre o tópico atual por e-mail.  Texto de direitos autorais para o conteúdo.  Definição de logotipo. |
| **Elemento** | **Valor (Essas strings podem ser modificadas para atender à necessidade do adotante de conteúdo.)** |
| Copyright | © 2013 Microsoft Corporation. Todos os direitos reservados. |
| EnviarFeedback | \<a{0}href=" {1} ">\<Enviar feedback /um> sobre este tópico para a Microsoft. |
| FeedbackLink | |
| LogotipoTítulo | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| LogoNome do arquivo | vs_logo_bk.gif |
| LogoFileNameHC | vs_logo_wh.gif |
| Recurso: | **Isenção de responsabilidade** |
| Use: | Um conjunto de isenções específicas de casos para conteúdo traduzido por máquina. |
| **Elemento** | **Valor** |
| MT_Editable | Este artigo foi traduzido por máquina. Se você tiver uma conexão com a Internet, selecione "Exibir este tópico on-line" para exibir esta página no modo editável com o conteúdo original em inglês ao mesmo tempo. |
| MT_NonEditable | Este artigo foi traduzido por máquina. Se você tiver uma conexão com a Internet, selecione "Exibir este tópico on-line" para exibir esta página no modo editável com o conteúdo original em inglês ao mesmo tempo. |
| MT_QualityEditable | Este artigo foi traduzido manualmente. Se você tiver uma conexão com a Internet, selecione "Exibir este tópico on-line" para exibir esta página no modo editável com o conteúdo original em inglês ao mesmo tempo. |
| MT_QualityNonEditable | Este artigo foi traduzido manualmente. Se você tiver uma conexão com a Internet, selecione "Exibir este tópico on-line" para exibir esta página no modo editável com o conteúdo original em inglês ao mesmo tempo. |
| MT_BetaContents | Este artigo foi traduzido para uma versão preliminar. Se você tiver uma conexão com a Internet, selecione "Exibir este tópico on-line" para exibir esta página no modo editável com o conteúdo original em inglês ao mesmo tempo. |
| MT_BetaRecycledContents | Este artigo foi traduzido manualmente para uma versão preliminar. Se você tiver uma conexão com a Internet, selecione "Exibir este tópico on-line" para exibir esta página no modo editável com o conteúdo original em inglês ao mesmo tempo. |
| Recurso: | **Tabela de link** |
| Use: | Suporte para links de tópicos on-line |
| **Elemento** | **Valor** |
| LinkTableTitle | Tabela de link |
| TopicEnuLinkText | Veja a\<versão em inglês /a> deste tópico que está disponível no seu computador. |
| TópicoOnlineLinkTexto | Veja este \<tópico a{0} {1} href=" ">online\</a> |
| OnlineText | Online |
| Recurso: | **Controle de áudio de vídeo** |
| Use: | Exibir elementos e texto para conteúdo de vídeo |
| **Elemento** | **Valor** |
| MultiMediaNotSupported | O Internet Explorer 9 ou superior {0} deve ser instalado para suportar conteúdo. |
| Videotext | exibindo vídeo |
| AudioText | streaming de áudio |
| OnlineVideoLinkText | \<p>Para visualizar o vídeo {0} \<associado a{1}este {2}tópico, clique em a href=" ">aqui\</a>. \</p> |
| OnlineAudioLinkText | \<p>Para ouvir o áudio associado {0} \<a este{1}tópico, clique em a href=" ">{2}aqui\</a>. \</p> |
| Recurso: | **Controle não instalado de conteúdo** |
| Use: | Elementos de texto (strings) usados para a renderização de conteúdonotinstalled.htm |
| **Elemento** | **Valor** |
| ConteúdoNãoinstaladoTítulo | Nenhum conteúdo foi encontrado no seu computador. |
| ConteúdoNãoinstaladoDownloadConteúdoTexto | \<p>Para baixar o \<conteúdo no{0} {1} seu computador,\<um href=" ">clique na guia Gerenciar /a>. \</p> |
| ConteúdoNãoinstaladoTexto | \<p>Nenhum conteúdo está instalado no seu computador. Consulte o administrador para obter a instalação local de conteúdo de ajuda. \</p> |
| Recurso: | **Controle tópico não encontrado** |
| Use: | Elementos de texto (strings) usados para a renderização de topicnotfound.htm |
| **Elemento** | **Valor** |
| TopicNotFoundTitle | Não é possível encontrar tópico solicitado em seu computador. |
| TópicoNão EncontradoVisãoOnlineTexto | \<p>O tópico que você solicitou não foi \<encontrado em{0} {1} seu computador,\<mas você pode a href=" ">ver o tópico on-line /a>. \</p> |
| TópicoNotFoundDownloadConteúdoTextoTexto | \<p>Consulte o painel de navegação \<para links{0}para {1} tópicos semelhantes, ou a href=" ">clique na guia\<Gerenciar /um> para baixar conteúdo para o seu computador. \</p> |
| TopicNotFoundText | \<p>O tópico que você solicitou não foi encontrado no seu computador. \</p> |
| Recurso: | **Tópico Controle Corrompido** |
| Use: | Elementos de texto (strings) usados para a renderização de topiccorrupted.htm |
| **Elemento** | **Valor** |
| TopicCorruptedTitle | Não é possível exibir o tópico solicitado. |
| TópicoCorruptedViewOnlineTexto | \<p>O Visualizador de Ajuda não pode exibir o tópico solicitado. Pode haver um erro no conteúdo do tópico ou uma dependência do sistema subjacente. \</p> |
| Recurso: | **Controle da página inicial** |
| Use: | Texto que suporta a exibição do conteúdo de nó de nível superior do Help Viewer. |
| **Elemento** | **Valor** |
| HomePageTitle | Ajude o Espectador em casa |
| HomePageIntrodução | \<p>Bem-vindo ao Microsoft Help Viewer, uma fonte essencial de informações para todos que usam ferramentas, produtos, tecnologias e serviços da Microsoft. O Help Viewer oferece acesso a informações de como fazer e referenciar, código de exemplo, artigos técnicos e muito mais. Para encontrar o conteúdo necessário, navegue pela tabela de conteúdos, use pesquisa de texto completo ou navegue pelo conteúdo usando o índice de palavras-chave. \</p> |
| HomePageContentInstallText | \<p \<>br />Use{0}o {1} \<href=" ">Gerenciar conteúdo\<\</uma> guia para fazer o seguinte: ul>\<li>Adicionar conteúdo ao seu computador. \</li \<>li>Verifique se há atualizações do seu conteúdo local. \</li \<>li>Remover conteúdo do seu computador. \</li \<>/ul>\</p> |
| HomePagePáginaLivros instalados | Livros Instalados |
| HomePageNoBooksInstalado | Nenhum conteúdo foi encontrado no seu computador. |
| HomePageHelpSettings | Ajudar as configurações de conteúdo |
| HomePageHelpSettingsTexto | \<p>Sua configuração atual é de ajuda local. O Visualizador de Ajuda exibe o conteúdo que você instalou no seu computador. \<br />Para alterar sua fonte de conteúdo de \<Ajuda, na{0}barra de menus\<do Visual Studio, escolha o estilo de extensão=" ">Ajuda, Defina preferência de ajuda /extensão>. \<>/p \<> |
| Megabyte | MB |

**branding.js**

O arquivo branding.js contém JavaScript usado pelos elementos de marca Visual Studio Help Viewer.  Abaixo está uma lista dos elementos da marca e da função JavaScript de suporte.  Todas as strings a serem localizadas para este arquivo são definidas na seção "Strings localizáveis" na parte superior deste arquivo.  O arquivo ICL foi criado para seqüências loc dentro do arquivo branding.js.

||||
|-|-|-|
|**Recurso de branding**|**Função JavaScript**|**Descrição**|
|Var...||Definir variáveis|
|Obtenha a linguagem de código do usuário|setUserPreferenceLang|mapeia um índice # para linguagem de código|
|Definir e obter valores de cookies|getCookie, setCookie||
|Membro Herdado|alterarMembrosRótulo|Membro herdado de expansão/colapso|
|Quando SelfBranded=False|Onload|Leia a seqüência de consultas para verificar se é uma solicitação de impressão.  Defina todos os codesnippets para focar a guia preferida do usuário.  Se for uma solicitação de impressão, então defina isPrinterFriendly para true. Verifique se há modo de alto contraste.|
|Snippet de código|adicionarSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||Tab de mudança||
||setCodesnippetLang||
||setCurrentLang||
||Copytoclipboard||
|Área dobrável|addToDoDoibleControlSet|escrever todo o objeto de controle dobrável em lista.|
||CA_Click|com base no estado da área dobrável, define qual imagem e texto apresentar|
|Suporte de contraste para logotipo|isBlackBackground()|Chamado para determinar se o fundo é preto.  Só preciso quando em modo de alto contraste.|
||isHighContrast()|usar um vão colorido para detectar modo de contraste alto|
||onHighContrast (preto)|Chamado quando o alto contraste é detectado|
|Funcionalidade LST|||
||addToLanSpecTextIdSet (id)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet(lang)||
|Funcionalidade multimídia|legenda (início, fim, texto, estilo)||
||findAllMediaControls (normalizadoId)||
||getActivePlayer (normalizadoId)||
||captionsOnOff(id)||
||toSeconds(t)||
||getAllComments(nó)||
||styleRectify (styleName, styleValue)||
||showCC(id)||
||legenda (id)||

**ARQUIVOS HTM**

O pacote de marca contém um conjunto de arquivos HTM que suportam cenários para comunicar informações-chave para ajudar usuários de conteúdo, por exemplo, uma página inicial que contém uma seção descrevendo quais conjuntos de conteúdo são instalados e páginas dizendo ao usuário quando os tópicos não podem ser encontrados no conjunto local de tópicos. Estes arquivos HTM podem ser modificados por produto.  Os fornecedores ISO Shell podem pegar o pacote de marca padrão e alterar o comportamento e o conteúdo dessas páginas para apegar suas necessidades.  Esses arquivos referem-se ao seu respectivo pacote de marca para que as tags de marca obtenham o conteúdo correspondente do arquivo branding.xml.

||||
|-|-|-|
|**Arquivo**|**Usar**|**Fonte de conteúdo exibida**|
|homepage.htm|Esta é uma página que exibe o conteúdo instalado atualmente e qualquer outra mensagem apropriada para apresentar ao usuário sobre seu conteúdo.  Este arquivo tem o atributo de meta dados adicional "Microsoft.Help.Id" conteúdo="-1" que coloca esse conteúdo na parte superior do TOC de conteúdo local.||
||<META_HOME_PAGE_TITLE_ADD META_HOME_PAGE_TITLE_ADD />|Branding.xml, \<tag HomePageTitle>|
||HOME_PAGE_INTRODUCTION_SECTION_ADD <>|Branding.xml, \<tag HomePageIntroduction>|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD />|Branding.xml, \<tag HomePageContentInstallText>|
||<> de HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD|Seção de títulos\<Branding.xml tag HomePageInstalledBooks \<>, os dados gerados a partir do aplicativo, HomePageNoBooksInstalado> quando nenhum livro é instalado.|
||<HOME_PAGE_SETTINGS_SECTION_ADD />|Seção de títuloS \<Branding.xml tag HomePageHelpSettings>, texto \<de seção HomePageHelpSettingsText>.|
|tópicoscorruptos.htm|Quando existe um tópico no conjunto local, mas por algum motivo não pode ser exibido (conteúdo corrompido).||
||<META_TOPIC_CORRUPTED_TITLE_ADD />|Branding.xml, \<tag TopicCorruptedTitle>|
||<TOPIC_CORRUPTED_SECTION_ADD />|Branding.xml, \<tag TopicCorruptedViewOnlineText>|
|topicnotfound.htm|Quando um tópico não é encontrado no conjunto de conteúdo local, nem disponível on-line||
||<META_TOPIC_NOT_FOUND_TITLE_ADD />|Branding.xml, \<tag TopicNotFoundTitle>|
||<META_TOPIC_NOT_FOUND_ID_ADD />|Branding.xml, \<tag TopicNotFoundViewOnlineText \<> + TopicNotFoundDownloadContentText>|
||<TOPIC_NOT_FOUND_SECTION_ADD >|Branding.xml, \<tag TopicNotFoundText>|
|contentnotinstalled.htm|Quando não há conteúdo local instalado para o produto.||
||META_CONTENT_NOT_INSTALLED_TITLE_ADD <>|Branding.xml, \<tag ContentNotInstalledTitle>|
||<> de META_CONTENT_NOT_INSTALLED_ID_ADD|Branding.xml, \<tag ContentNotInstalledDownloadContentText>|
||<CONTENT_NOT_INSTALLED_SECTION_ADD CONTENT_NOT_INSTALLED_SECTION_ADD >|Branding.xml, \<tag ContentNotInstalledText>|

**Arquivos CSS**

O Visual Studio Help Viewer Branding Package contém dois arquivos css para suportar a apresentação consistente de conteúdo do Visual Studio Help:

- Branding.css - contém elementos css para renderização onde SelfBranded=false

- Printer.css - contém elementos css para renderização onde SelfBranded=false

Os arquivos branding.css incluem definições para apresentação de tópicos do Visual Studio\<(ressalva é que o branding.css contido no local de Branding_>.mshc do serviço de pacotes pode mudar).

**Arquivos gráficos**

O conteúdo do Visual Studio exibe um logotipo do Visual Studio, bem como outros gráficos.  A lista completa de arquivos gráficos no pacote de marca Visual Studio Help Viewer é mostrada abaixo.

||||
|-|-|-|
|**Arquivo**|**Usar**|**Exemplos**|
|clear.gif|Usado para renderizar área dobrável||
|footer_slice.gif|Apresentação de rodapé||
|info_icon.gif|Usado ao exibir informações|Isenção de responsabilidade|
|online_icon.gif|Este ícone deve ser associado a links on-line||
|tabLeftBD.gif|Usado para renderizar o recipiente de snippet de código||
|tabRightBD.gif|Usado para renderizar o recipiente de snippet de código||
|vs_logo_bk.gif|Usado para referências normais de logotipo de \<contraste, conforme definido em Branding.xml tag LogoFileName>.  Para os produtos Visual Studio, o nome do logotipo é vs_logo_bk.gif.||
|vs_logo_wh.gif|Usado para referências normais de logotipo alto, conforme definido em Branding.xml tag \<LogoFileNameHC>.  Para os produtos Visual Studio, o nome do logotipo é vs_logo_wh.gif.||
|ccOff.png|Gráfico de legendas||
|ccOn.png|Gráfico de legendas||
|ImageSprite.png|Usado para renderizar área dobrável|gráfico expandido ou colapso|

## <a name="deploy-a-set-of-topics"></a>Implantar um conjunto de tópicos

Este é um tutorial simples e rápido para criar um conjunto de implantação de conteúdo do Help Viewer composto por um arquivo MSHA e o conjunto de táxis ou MSHCs contendo os tópicos. O MSHA é um arquivo XML que descreve um conjunto de táxis ou arquivos MSHC. O Visualizador de Ajuda pode ler o MSHA para obter uma lista de conteúdo (o . CAB ou . Arquivos MSHC) disponíveis para instalação local.

Este é apenas um primer descrevendo o esquema XML muito básico para o Help Viewer MSHA.  Há um exemplo de implementação abaixo desta breve visão geral e a amostra HelpContentSetup.msha.

O nome do MSHA, para efeitos deste primer, é HelpContentSetup.msha (o nome do arquivo pode ser qualquer coisa, com a extensão . MSHA). HelpContentSetup.msha (exemplo abaixo) deve conter uma lista das cabines ou MSHCs disponíveis.  O tipo de arquivo deve ser consistente dentro do MSHA (não suporta uma combinação de tipos de arquivo MSHA e CAB). Para cada CAB ou MSHC, \<deve haver uma div class="pacote">... \</div> (veja exemplo abaixo).

Nota: no exemplo de implementação abaixo, incluímos o pacote de marca. Isso é fundamental para incluir, a fim de obter os elementos de renderização de conteúdo do Visual Studio necessários e comportamentos de conteúdo.

Amostra de ajudaConteúdoSetup.msha arquivo: (Substitua "nome do conjunto de conteúdo 1" e "nome do conjunto de conteúdo 2" etc. com os nomes dos arquivos.)

```html
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>.
```

1. Criar pasta local, algo como "C:\SampleContent"

2. Para este exemplo, usaremos arquivos MSHC para conter os tópicos.  Um MSHC é um zip com a extensão de arquivo alterada de .zip para . MSHC.

3. Crie o HelpContentSetup.msha abaixo como um arquivo de texto (o bloco de notas foi usado para criar o arquivo) e salve-o na pasta acima mencionada (ver etapa 1).

A classe "Branding" existe e é única. A marca mshc está incluída nesta cartilha para que o conteúdo instalado tenha marca, e os comportamentos de conteúdo contidos nos MSHCs terão os elementos de suporte apropriados contidos no pacote de marca. Sem isso, os erros resultarão quando o sistema procura itens de suporte que não fazem parte do conteúdo rasgado (instalado).

Para obter o pacote de marca Visual Studio, copie Branding_en arquivo US.mshc em C:\Arquivos de programa (x86)\Microsoft Help Viewer\v2.3\ para sua pasta de trabalho.

```html
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>
<div class="package">
<span class="packageType">branding</span>
<span class="name">Branding_en-US</span>
<span class="deployed">True</span>
<a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a>
</div>
</div>
</body>
</html>
```

**Resumo**

O uso e a extensão das etapas acima permitirão que os VSPs implantem seus conjuntos de conteúdo para o Visual Studio Help Viewer.

### <a name="add-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Adicione ajuda ao Visual Studio Shell (Integrado e Isolado)

**Introdução**

Este passo a passo demonstra como incorporar o conteúdo do Help em um aplicativo Visual Studio Shell e, em seguida, implantá-lo.

**Requisitos**

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2. [Visual Studio 2013 Shell Redist Isolado](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

**Visão geral**

O [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell é uma [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] versão do IDE na qual você pode basear uma aplicação. Tais aplicações contêm o Shell isolado juntamente com extensões que você cria. Use modelos de projeto Shell isolados, que estão incluídos no [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] SDK, para construir extensões.

As etapas básicas para criar um aplicativo isolado baseado em Shell e sua ajuda:

1. Obtenha [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] o ISO Shell redistributable (um download da Microsoft).

2. No Visual Studio, crie uma extensão de Ajuda baseada na Shell Isolada, por exemplo, a extensão Contoso Help que é descrita posteriormente neste passo a passo.

3. Enrole a extensão e o ISO Shell seja avermelhado em um MSI de implantação (uma configuração de aplicativo). Este passo a passo não inclui uma etapa de configuração.

Crie uma loja de conteúdo do Visual Studio. Para o cenário Shell Integrado, mude o Visual Studio12 para o nome do catálogo do produto da seguinte forma:

- Criar pasta C:\ProgramData\Microsoft\HelpLibrary2\Catálogos\VisualStudio15.

- Crie um arquivo chamado CatalogType.xml e adicione-o à pasta. O arquivo deve conter as seguintes linhas de código:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

Defina a loja de conteúdo no registro. Para a Shell Integrada, mude o VisualStudio15 para o nome do catálogo do produto:

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catálogos\VisualStudio15

   Chave: Valor da seqüência do LocationPath: C:\ProgramData\Microsoft\HelpLibrary2\Catálogos\VisualStudio15\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catálogos\VisualStudio15\en-US

   Chave: Valor da [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] string catalogname: documentação

**Criar o Projeto**

Para criar uma extensão Shell isolada:

1. No Visual Studio, em **File,** escolha **Novo Projeto,** em **Outros Tipos de Projeto** escolha **Extensibility**e escolha **Visual Studio Shell Isolated**. Nomeie `ContosoHelpShell`o projeto ) para criar um projeto de extensibilidade baseado no modelo Visual Studio Isolated Shell.

2. No Solution Explorer, no projeto ContosoHelpShellUI, na pasta Arquivos de recursos, abra ApplicationCommands.vsct. Certifique-se de que esta linha seja comentada (procure por "No_Help"):`<!-- <define name="No_HelpMenuCommands"/> -->`

3. Escolha a tecla F5 para compilar e executar **o Debug**. No caso experimental do IDE Shell Isolado, escolha o menu **Ajuda.** Certifique-se de que os comandos **'Exibir ajuda',** **adicionar e remover conteúdo de ajuda'** e definir a preferência de **ajuda** serão exibidos.

4. No Solution Explorer, no projeto ContosHelpShell, na pasta De Personalização shell, abra ContosoHelpShell.pkgdef. Para definir o catálogo de Ajuda contoso, adicione as seguintes linhas:

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5. No Solution Explorer, no projeto ContosHelpShell, na pasta De personalização shell, abra ContosoHelpShell.Application.pkgdef. Para ativar a Ajuda f1, adicione as seguintes linhas:

    ```
    // F1 Help Provider

    [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
    "Name"="13407"
    "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}"
    @="Help3 Provider"
    [$RootKey$\HelpProviders]
    @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}"
    [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
    "Name"="Help3 Provider"
    @="{4A791146-19E4-11D3-B86B-00C04F79F802}"
    ```

6. No Solution Explorer, no menu de contexto da solução ContosoHelpShell, escolha o item do menu **Propriedades.** Em **Propriedades de configuração,** selecione **Gerenciador de configuração**. Na coluna **Configuração,** altere cada valor "Depuração" para "Liberar".

7. Compile a solução. Isso cria um conjunto de arquivos em uma pasta de versão, que será usado na próxima seção.

Para testar isso como se estivesse implantado:

1. Na máquina que você está implantando Contoso para, instalar o ISO Shell baixado (de cima).

2. Crie uma \\pasta em \Arquivos de\\programa (x86) e nomeie-a `Contoso`.

3. Copie o conteúdo da pasta de \\versão ContosoHelpShell para \Arquivos do programa (x86)\Contoso\\ pasta.

4. Inicie o Editor de Registro escolhendo `Regedit` **Executar** no menu **Iniciar** e inserindo . No editor de registro, escolha **Arquivo**e, em seguida, **Importar**. Navegue até a pasta do projeto ContosoHelpShell. Na subpasta ContosoHelpShell, escolha ContosoHelpShell.reg.

5. Criar uma loja de conteúdo:

    Para ISO Shell - crie uma loja de conteúdo Contoso C:\ProgramData\Microsoft\HelpLibrary2\Catálogos\ContosoDev12

    Para [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] shell integrado, crie a pasta C:\ProgramData\Microsoft\HelpLibrary2\Catálogos\VisualStudio15

6. Crie catalogType.xml e adicione à loja de conteúdo (etapa anterior) que contém:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. Adicione as seguintes chaves de registro:

    HKLM\SOFTWARE\WOW6432Node\Microsoft\Help\v2.3\Catálogos\VisualStudio15Chave: Valor da string do LocationPath:

    Para a concha ISO:

    C:ProgramDataMicrosoftHelpLibrary2CatálogosVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]Shell integrado:

    C:ProgramDataMicrosoftHelpLibrary2CatálogosVisualStudio15en-US

    Chave: CatalogName String [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] value: Documentation. Para iso shell, este é o nome do seu catálogo.

8. Copie seu conteúdo (táxis ou MSHC e MSHA) para uma pasta local.

9. Exemplo linha de comando Shell integrada para testar armazenamento de conteúdo. Para iso shell, altere o catálogo e os valores de Lançamentoapp conforme apropriado para combinar com o produto.

     "C:\Arquivos de programa (x86)\Microsoft Help Viewer\v2.3\HlpViewer.exe" /catalogName VisualStudio15 /helpQuery method="page&id=ContosoTopic0" /launchingApp Microsoft,VisualStudio,12.0

10. Inicie o aplicativo Contoso (a partir da raiz do aplicativo Contoso). No ISO Shell, escolha o item do menu **Ajuda** e altere a **preferência de ajuda** definida para usar ajuda **local**.

11. Dentro da concha, escolha o item **''''Ajuda'** e, em seguida, **exibir ajuda**. O visualizador local de ajuda deve ser lançado. Escolha a guia **Gerenciar conteúdo.** Em **'Origem de instalação',** escolha o botão De opção **Disco.** Escolha o **botão ...** e navegue até a pasta local contendo conteúdo contoso (copiado para a pasta local na etapa acima). Escolha o HelpContentSetup.msha. Contoso agora deve aparecer como um livro nas seleções de livros. Escolha **Adicionar**e, em seguida, escolha o botão **Atualizar** (canto inferior direito).

12. Dentro do Contoso IDE, escolha a chave da F1 para testar a funcionalidade da F1.

## <a name="additional-resources"></a>Recursos adicionais

Para obter a API de tempo de execução, consulte [a API de ajuda do Windows](/previous-versions/windows/desktop/helpapi/helpapi-portal).

Para obter mais informações sobre como aproveitar a API de ajuda, consulte [exemplos de código do Help Viewer](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples).

Você pode enviar sugestões de recursos sobre [a Comunidade de Desenvolvedores](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).

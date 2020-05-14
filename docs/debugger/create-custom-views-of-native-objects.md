---
title: Criar exibições personalizadas dos objetos de C++
description: Use a estrutura Natvis para personalizar a maneira como o Visual Studio exibe tipos nativos no depurador
ms.date: 03/02/2020
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 4f8bdd8d26ba450b1aedd790d644c183607c44af
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224505"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Crie visualizações personalizadas de objetos C++ no depurador usando a estrutura Natvis

A estrutura do Visual Studio *Natvis* personaliza a forma como os tipos nativos aparecem em janelas variáveis de depurador, como as janelas **Locais** e **Watch,** e em **DataTips**. As visualizações de Natvis podem ajudar a tornar os tipos que você cria mais visíveis durante a depuração.

O Natvis substitui o arquivo *autoexp.dat* em versões anteriores do Visual Studio com sintaxe XML, melhor diagnóstico, versionamento e suporte a vários arquivos.

> [!NOTE]
> As personalizações natvis funcionam com classes e estruturas, mas não digitadas.

## <a name="natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a>Visualizações de Natvis

Você usa a estrutura Natvis para criar regras de visualização para os tipos que você cria, para que os desenvolvedores possam vê-los mais facilmente durante a depuração.

Por exemplo, a ilustração a seguir mostra uma variável do tipo [Windows::UI::Xaml::Controles::TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) em uma janela de depurador sem quaisquer visualizações personalizadas aplicadas.

![Visualização padrão do TextBox](../debugger/media/dbg_natvis_textbox_default.png "Visualização padrão do TextBox")

A linha destacada mostra a `Text` propriedade da `TextBox` classe. A complexa hierarquia de classes dificulta encontrar essa propriedade. O depurador não sabe como interpretar o tipo de string personalizado, então você não pode ver a seqüência mantida dentro da caixa de texto.

O `TextBox` mesmo parece muito mais simples na janela variável quando as regras de visualizadores personalizados natvis são aplicadas. Os membros importantes da classe aparecem juntos, e o depurador mostra o valor de seqüência subjacente do tipo de string personalizado.

![Dados do TextBox usando o visualizador](../debugger/media/dbg_natvis_textbox_visualizer.png "Dados do TextBox usando o visualizador")

## <a name="use-natvis-files-in-c-projects"></a><a name="BKMK_Using_Natvis_files"></a>Use arquivos .natvis em projetos C++

O Natvis usa arquivos *.natvis* para especificar regras de visualização. Um arquivo *.natvis* é um arquivo XML com uma extensão *.natvis.* O esquema Natvis é definido em *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd*.

A estrutura básica de um arquivo *.natvis* é um ou mais `Type` elementos representando entradas de visualização. O nome totalmente `Type` qualificado de cada `Name` elemento é especificado em seu atributo.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
  <Type Name="MyNamespace::CFoo">
    .
    .
  </Type>

  <Type Name="...">
    .
    .
  </Type>
</AutoVisualizer>
```

O Visual Studio fornece alguns arquivos *.natvis* na pasta *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers.* Esses arquivos têm regras de visualização para muitos tipos comuns, e podem servir de exemplos para escrever visualizações para novos tipos.

### <a name="add-a-natvis-file-to-a-c-project"></a>Adicione um arquivo .natvis a um projeto C++

Você pode adicionar um arquivo *.natvis* a qualquer projeto C++.

**Para adicionar um novo arquivo *.natvis:***

1. Selecione o nó de projeto C++ no **Solution Explorer**e selecione **Project** > **Add new item**ou clique com o botão direito do mouse no projeto e selecione **Adicionar** > **novo item**.

1. Na **caixa de diálogo Adicionar novo item,** selecione o arquivo de visualização do Depurador de**utilidades** >  **Visual C++** > **(.natvis)**.

1. Nomeie o arquivo e **selecione Adicionar**.

   O novo arquivo é adicionado ao **Solution Explorer**e é aberto no painel de documentos do Visual Studio.

O depurador do Visual Studio carrega arquivos *.natvis* em projetos C++ automaticamente e, por padrão, também os inclui no arquivo *.pdb* quando o projeto é construído. Se você depurar o aplicativo construído, o depurador carregará o arquivo *.natvis* do arquivo *.pdb,* mesmo que você não tenha o projeto aberto. Se você não quiser que o arquivo *.natvis* seja incluído no *.pdb,* você pode excluí-lo do arquivo *.pdb* construído.

**Para excluir um arquivo *.natvis* de um *.pdb*:**

1. Selecione o arquivo *.natvis* no **Solution Explorer**e selecione o ícone **Propriedades** ou clique com o botão direito do mouse no arquivo e selecione **Propriedades**.

1. Baixe a seta ao lado de **Excluído de 'Criar'** e **selecione 'Sim'** e, em seguida, selecione **OK**.

>[!NOTE]
>Para depurar projetos executáveis, use os itens da solução para adicionar quaisquer arquivos *.natvis* que não estejam no *.pdb,* já que não há nenhum projeto C++ disponível.

>[!NOTE]
>As regras natvis carregadas a partir de um *.pdb* aplicam-se apenas aos tipos nos módulos a que o *.pdb* se refere. Por exemplo, se *o Module1.pdb* tiver uma `Test`entrada Natvis para `Test` um tipo chamado, ele só se aplica à classe no *Module1.dll*. Se outro módulo também definir `Test`uma classe nomeada, a entrada *Module1.pdb* Natvis não se aplica a ela.

**Para instalar e registrar um arquivo *.natvis* através de um pacote VSIX:**

Um pacote VSIX pode instalar e registrar arquivos *.natvis.* Não importa onde eles estão instalados, todos os arquivos *.natvis* registrados são automaticamente captados durante a depuração.

1. Inclua o arquivo *.natvis* no pacote VSIX. Por exemplo, para o seguinte arquivo de projeto:
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. Registre o arquivo *.natvis* no arquivo *source.extension.vsixmanifest:*
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="natvis-file-locations"></a><a name="BKMK_natvis_location"></a>Localizações de arquivos Natvis

Você pode adicionar arquivos *.natvis* ao seu diretório de usuário ou a um diretório do sistema, se quiser que eles se inscrevam em vários projetos.

Os arquivos *.natvis* são avaliados na seguinte ordem:

1. Quaisquer arquivos *.natvis* que estejam incorporados em um *.pdb* você está depurando, a menos que um arquivo de mesmo nome exista no projeto carregado.

2. Quaisquer arquivos *.natvis* que estejam em um projeto C++ carregado ou uma solução de nível superior. Este grupo inclui todos os projetos C++ carregados, incluindo bibliotecas de classe, mas não projetos em outros idiomas.

3. Todos os arquivos *.natvis* instalados e registrados através de um pacote VSIX.

::: moniker range="vs-2017"

4. O diretório Natvis específico do usuário (por exemplo, *%USERPROFILE%\Documents\Visual Studio 2017\Visualizers*).

::: moniker-end

::: moniker range=">= vs-2019"

4. O diretório Natvis específico do usuário (por exemplo, *%USERPROFILE%\Documents\Visual Studio 2019\Visualizers*).

::: moniker-end

5. O diretório Natvis em todo o sistema *(%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Este diretório tem os arquivos *.natvis* que são instalados com o Visual Studio. Se você tiver permissões de administrador, você pode adicionar arquivos a este diretório.

## <a name="modify-natvis-files-while-debugging"></a>Modificar arquivos .natvis durante a depuração

Você pode modificar um arquivo *.natvis* no IDE enquanto depura seu projeto. Abra o arquivo na mesma instância do Visual Studio com o que você está depurando, modifique-o e salve-o. Assim que o arquivo é salvo, o **Relógio** e **os Locais** atualizam as janelas para refletir a alteração.

Você também pode adicionar ou excluir arquivos *.natvis* em uma solução que você está depurando, e o Visual Studio adiciona ou remove as visualizações relevantes.

Você não pode atualizar arquivos *.natvis* que estão incorporados em arquivos *.pdb* enquanto você está depurando.

Se você modificar o arquivo *.natvis* fora do Visual Studio, as alterações não terão efeito automaticamente. Para atualizar as janelas de depurador, você pode reavaliar o comando **.natvisreload** na janela **Imediato.** Em seguida, as alterações entrarão em vigor sem reiniciar a sessão de depuração.

Use também o comando **.natvisreload** para atualizar o arquivo *.natvis* para uma versão mais recente. Por exemplo, o arquivo *.natvis* pode ser verificado no controle de origem, e você deseja pegar as alterações recentes que outra pessoa fez.

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a> Expressões e formatação
As visualizações do Natvis usam expressões do C++ para especificar os itens de dados a serem exibidos. Além dos aprimoramentos e limitações das expressões C++ no depurador, que são descritos no Operador de [Contexto (C++)](../debugger/context-operator-cpp.md), esteja ciente do seguinte:

- As expressões do Natvis são avaliadas no contexto do objeto que está sendo visualizado, não do registro de ativação atual. Por exemplo, `x` em uma expressão Natvis refere-se ao campo chamado **x** no objeto que está sendo visualizado, não a uma variável local chamada **x** na função atual. Você não pode acessar variáveis locais em expressões Natvis, embora você possa acessar variáveis globais.

- As expressões natvis não permitem avaliação de funções ou efeitos colaterais. Chamadas de função e operadores de atribuição são ignorados. Como as [funções intrínsecas do depurador](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) não têm efeitos colaterais, elas podem ser livremente chamadas de qualquer expressão do natvis, mesmo que outras chamadas de função estejam desabilitadas.

- Para controlar como uma expressão é exibida, você pode usar qualquer um dos especificadores de formato descritos em [especificadores de formato em C++](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers). Os especificadores de formato são ignorados quando a entrada é `Size` usada internamente pelo Natvis, como a expressão em uma [expansão ArrayItems](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).

## <a name="natvis-views"></a>Natvis visualizações

Você pode definir diferentes visualizações natvis para exibir tipos de diferentes maneiras. Por exemplo, aqui está `std::vector` uma visualização que define `simple`uma visão simplificada chamada . Os `DisplayString` `ArrayItems` elementos e os elementos `simple` aparecem na `[size]` `[capacity]` exibição padrão e na `simple` exibição, enquanto os itens e itens não aparecem na exibição.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

Na janela **Relógio,** use o especificador de formato **de exibição** para especificar uma exibição alternativa. A visão simples aparece como **vec,view(simples):**

![Janela do relógio com vista simples](../debugger/media/watch-simpleview.png "Janela do relógio com vista simples")

## <a name="natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a>Erros de Natvis

Quando o depurador encontra erros em uma entrada de visualização, ele os ignora. Ele exibe o tipo em sua forma bruta, ou escolhe outra visualização adequada. Você pode usar os diagnósticos do Natvis para entender por que o depurador ignorou uma entrada de visualização e ver erros de sintaxe e análise subjacentes.

**Para ativar os diagnósticos de Natvis:**

- Em **Opções de** > **ferramentas** (ou**opções** **de depuração)** > > janela de**saída** **de depuração,** > definir **mensagens de diagnóstico Natvis (somente C++ para** **Erro,** **Aviso**ou **Verbose,** e, em seguida, selecionar **OK**.

Os erros aparecem na **janela Saída.**

## <a name="natvis-syntax-reference"></a><a name="BKMK_Syntax_reference"></a>Referência de sintaxe natvis

### <a name="autovisualizer-element"></a><a name="BKMK_AutoVisualizer"></a> Elemento AutoVisualizer
O `AutoVisualizer` elemento é o nó raiz do arquivo *.natvis* e contém o atributo namespace. `xmlns:`

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

O `AutoVisualizer` elemento pode ter crianças [Type,](#BKMK_Type) [HResult,](#BKMK_HResult) [UIVisualizer](#BKMK_UIVisualizer)e [CustomVisualizer.](#BKMK_CustomVisualizer)

### <a name="type-element"></a><a name="BKMK_Type"></a>Elemento de tipo

Um `Type` básico se parece com este exemplo:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 O `Type` elemento especifica:

1. Para que tipo a visualização `Name` deve ser usada (o atributo).

2. Qual deve ser a aparência de um objeto desse tipo (semelhante à do elemento `DisplayString`).

3. Como os membros do tipo devem se parecer quando o usuário `Expand` expande o tipo em uma janela variável (o nó).

#### <a name="templated-classes"></a>Classes modeladas
O `Name` atributo `Type` do elemento aceita `*` um asterisco como um caractere curinga que pode ser usado para nomes de classes modeladas.

No exemplo a seguir, a mesma visualização `CAtlArray<int>` é `CAtlArray<float>`usada se o objeto é um ou um . Se há uma entrada de visualização específica para a, `CAtlArray<float>`então ela tem precedência sobre a genérica.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

Você pode referenciar parâmetros de modelo na entrada de visualização usando macros $T1, $T2 e assim por diante. Para localizar exemplos dessas macros, confira os arquivos *.natvis* que acompanham o Visual Studio.

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a> Correspondência de tipo de visualizador
Se uma entrada de visualização não for validada, a próxima visualização disponível será usada.

#### <a name="inheritable-attribute"></a>Atributo hereditário
O `Inheritable` atributo opcional especifica se uma visualização se aplica apenas a um tipo de base, ou a um tipo de base e a todos os tipos derivados. O valor padrão de `Inheritable` é `true`.

No exemplo a seguir, a visualização `BaseClass` aplica-se apenas ao tipo:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Atributo de prioridade

O `Priority` atributo opcional especifica a ordem em que usar definições alternativas, se uma definição não analisar. Os valores `Priority` possíveis `Low` `MediumLow`são: `MediumHigh`, `High`,`Medium`, e . O valor padrão é `Medium`. O `Priority` atributo distingue apenas entre as prioridades dentro do mesmo arquivo *.natvis.*

O exemplo a seguir analisa primeiro a entrada que corresponde ao STL 2015. Se isso não for analisado, ele usa a entrada alternativa para a versão 2013 do STL:

```xml
<!-- VC 2013 -->
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">
     <DisplayString>{_Callee}</DisplayString>
    <Expand>
        <ExpandedItem>_Callee</ExpandedItem>
    </Expand>
</Type>

<!-- VC 2015 -->
<Type Name="std::reference_wrapper&lt;*&gt;">
    <DisplayString>{*_Ptr}</DisplayString>
    <Expand>
        <Item Name="[ptr]">_Ptr</Item>
    </Expand>
</Type>
```

### <a name="optional-attribute"></a>Atributo opcional
Você pode `Optional` colocar um atributo em qualquer nó. Se uma subexpressão dentro de um nó opcional não analisar, o depurador ignora `Type` esse nó, mas aplica o resto das regras. No tipo a `[State]` seguir, não `[Exception]` é opcional, mas é opcional.  Se `MyNamespace::MyClass` tiver um`M_exceptionHolder`campo chamado `[State]` _ , `[Exception]` tanto o nó quanto o `_M_exceptionHolder` nó aparecem, mas se não houver campo, apenas o `[State]` nó aparece.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a> Atributo de condição

O `Condition` atributo opcional está disponível para muitos elementos de visualização e especifica quando usar uma regra de visualização. Se a expressão dentro do `false`atributo da condição se resolver, a regra de visualização não se aplica. Se ele avaliar `true`, ou `Condition` não há atributo, a visualização se aplica. Você pode usar este atributo para a lógica if-else nas entradas de visualização.

Por exemplo, a visualização `DisplayString` a seguir tem dois elementos para um tipo de ponteiro inteligente. Quando `_Myptr` o membro está vazio, `DisplayString` a condição `true`do primeiro elemento se resolve para , de modo que a forma é exibida. Quando `_Myptr` o membro não está vazio, `false`a condição `DisplayString` avalia e o segundo elemento é exibido.

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

### <a name="includeview-and-excludeview-attributes"></a>IncluirExibir e excluir atributos

Os `IncludeView` `ExcludeView` atributos especificam elementos para exibir ou não exibir em exibições específicas. Por exemplo, na especificação `std::vector`Natvis `simple` a seguir, a `[size]` `[capacity]` exibição não exibe os itens e itens.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

Você pode `IncludeView` usar `ExcludeView` os atributos e atributos em tipos e em membros individuais.

### <a name="version-element"></a><a name="BKMK_Versioning"></a>Elemento de versão
O `Version` elemento possui uma entrada de visualização para um módulo e versão específicos. O `Version` elemento ajuda a evitar colisões de nomes, reduz incompatibilidades inadvertidas e permite diferentes visualizações para diferentes versões do tipo.

Se um arquivo de cabeçalho comum usado por diferentes módulos definir um tipo, a visualização em versão será exibida somente quando o tipo estiver na versão do módulo especificada.

No exemplo a seguir, a visualização `DirectUI::Border` é aplicável `Windows.UI.Xaml.dll` apenas para o tipo encontrado na versão 1.0 a 1.5.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

Você não precisa `Min` dos `Max`dois e. São atributos opcionais. Nenhum personagem curinga é suportado.

O `Name` atributo está no formato *filename.ext*, como *hello.exe* ou *some.dll*. Não são permitidos nomes de caminhos.

### <a name="displaystring-element"></a><a name="BKMK_DisplayString"></a>Elemento DisplayString
O `DisplayString` elemento especifica uma string para mostrar como o valor de uma variável. Aceita cadeias de caracteres arbitrárias misturadas a expressões. Tudo dentro de chaves é interpretado como uma expressão. Por exemplo, `DisplayString` a seguinte entrada:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Significa que variáveis `CPoint` de exibição de tipo como nesta ilustração:

 ![Use um elemento DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "Use um elemento DisplayString")

Na `DisplayString` expressão, `x` `y`e , que `CPoint`são membros de , estão dentro de chaves, de modo que seus valores são avaliados. O exemplo também mostra como você pode escapar de uma `{{` cinta `}}` encaracolada usando aparelhos cacheados duplos (ou ).

> [!NOTE]
> O `DisplayString` elemento é o único elemento que aceita cordas arbitrárias e sintaxe de cinta encaracolada. Todos os outros elementos de visualização aceitam apenas expressões que o depurador pode avaliar.

### <a name="stringview-element"></a><a name="BKMK_StringView"></a>Elemento StringView

O `StringView` elemento define um valor que o depurador pode enviar para o visualizador de texto incorporado. Por exemplo, dada a `ATL::CStringT` seguinte visualização para o tipo:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

O `CStringT` objeto é exibido em uma janela variável como este exemplo:

![Elemento CStringT DisplayString](../debugger/media/dbg_natvis_displaystring_cstringt.png "Elemento CStringT DisplayString")

Adicionar `StringView` um elemento diz ao depurador que ele pode exibir o valor como uma visualização de texto.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Durante a depuração, você pode selecionar o ícone de lupa ao lado da variável e, em seguida, selecionar **Visualizador de texto** para exibir a string que **m_pszData** aponta.

 ![Dados do CStringT com visualizador StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "Dados do CStringT com visualizador StringView")

A `{m_pszData,su}` expressão inclui um especificador de formato C++ **para**exibir o valor como uma seqüência de string Unicode. Para obter mais informações, consulte [Especificadores de formato em C++](../debugger/format-specifiers-in-cpp.md).

### <a name="expand-element"></a><a name="BKMK_Expand"></a>Elemento expandir

O `Expand` nó opcional personaliza as crianças de um tipo visualizado quando você expande o tipo em uma janela variável. O `Expand` nó aceita uma lista de nódulos infantis que definem os elementos da criança.

- Se `Expand` um nó não for especificado em uma entrada de visualização, as crianças usarão as regras de expansão padrão.

- Se `Expand` um nó for especificado sem nó sem nó infantil sob ele, o tipo não será expansível nas janelas do depurador.

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a> Expansão de item

 O `Item` elemento é o elemento mais `Expand` básico e comum em um nó. `Item` define um único elemento filho. Por exemplo, `CRect` uma `top`classe `left` `right`com `bottom` campos , e tem a seguinte entrada de visualização:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

Na janela de depurador, o `CRect` tipo se parece com este exemplo:

![CRect com expansão do elemento item](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect com expansão do elemento item")

O depurador avalia as expressões `Width` especificadas nos elementos e `Height` mostra os valores na coluna **Valor** da janela variável.

O depurador cria automaticamente o nó **[Raw View]** para cada expansão personalizada. A captura de tela anterior exibe o nó **[Raw View]** expandido, para mostrar como a visualização bruta padrão do objeto difere de sua visualização Natvis. A expansão padrão cria uma subárvore para a classe base e lista todos os membros de dados da classe base como crianças.

> [!NOTE]
> Se a expressão do elemento item aponta para um tipo complexo, o próprio nó **item** será expansível.

#### <a name="arrayitems-expansion"></a><a name="BKMK_ArrayItems_expansion"></a> Expansão de ArrayItems
Use o nó `ArrayItems` para que o depurador do Visual Studio interprete o tipo como uma matriz e exiba seus elementos individuais. A visualização `std::vector` é um bom exemplo:

```xml
<Type Name="std::vector&lt;*&gt;">
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mylast - _Myfirst</Item>
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>
    <ArrayItems>
      <Size>_Mylast - _Myfirst</Size>
      <ValuePointer>_Myfirst</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

Um `std::vector` mostra os elementos individuais quando expandido na janela variável:

![dst::vetor usando a expansão ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "dst::vetor usando a expansão ArrayItems")

O `ArrayItems` nó deve ter:

- Uma expressão `Size` (que deve ser avaliada como um inteiro) para que o depurador entenda o comprimento da matriz.
- Uma `ValuePointer` expressão que aponta para o primeiro elemento (que deve `void*`ser um ponteiro de um tipo de elemento que não é ).

O valor padrão do limite inferior da matriz é 0. Para substituir o valor, `LowerBound` use um elemento. Os arquivos *.natvis* enviados com o Visual Studio têm exemplos.

>[!NOTE]
>Você pode `[]` usar o `vector[i]`operador, por exemplo, com qualquer `ArrayItems`visualização de matriz unidimensional que use, mesmo que o próprio tipo (por exemplo) `CATLArray`não permita este operador.

Você também pode especificar matrizes multidimensionais. Nesse caso, o depurador precisa de um pouco mais de informações para exibir adequadamente elementos da criança:

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Direction>Forward</Direction>
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

- `Direction`especifica se a matriz está em linha maior ou ordem de coluna-maior.
- `Rank` especifica a classificação da matriz.
- O elemento `Size` aceita o parâmetro implícito `$i`, que ele substitui pelo índice de dimensão para descobrir o tamanho da matriz na dimensão. No exemplo anterior, `_M_extent.M_base[0]` a expressão deve dar o `_M_extent._M_base[1]` comprimento da 0ª dimensão, a 1ª, e assim por diante.

Veja como um objeto `Concurrency::array` bidimensional fica na janela do depurador:

![Matriz bidimensional com expansão ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "Matriz bidimensional com expansão ArrayItems")

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a> Expansão de IndexListItems

Você só `ArrayItems` pode usar a expansão se os elementos da matriz forem dispostos contíguamente na memória. O depurador chega ao próximo elemento simplesmente incrementando seu ponteiro. Se você precisar manipular o índice para `IndexListItems` o nó de valor, use nós. Aqui está uma visualização `IndexListItems` com um nó:

```xml
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_M_vector._M_index</Item>
    <IndexListItems>
      <Size>_M_vector._M_index</Size>
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>
    </IndexListItems>
  </Expand>
</Type>
```

A única `ArrayItems` diferença `IndexListItems` entre `ValueNode`e é o , que espera a `$i` expressão completa para o elemento i<sup>com</sup> o parâmetro implícito.

>[!NOTE]
>Você pode `[]` usar o `vector[i]`operador, por exemplo, com qualquer `IndexListItems`visualização de matriz unidimensional que use, mesmo que o próprio tipo (por exemplo) `CATLArray`não permita este operador.

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a> Expansão de LinkedListItems

Se o tipo visualizado representa uma lista vinculada, o depurador pode exibir seus filhos usando um nó `LinkedListItems`. A visualização a `CAtlList` seguir `LinkedListItems`para o tipo usa:

```xml
<Type Name="ATL::CAtlList&lt;*,*&gt;">
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>
  <Expand>
    <Item Name="Count">m_nElements</Item>
    <LinkedListItems>
      <Size>m_nElements</Size>
      <HeadPointer>m_pHead</HeadPointer>
      <NextPointer>m_pNext</NextPointer>
      <ValueNode>m_element</ValueNode>
    </LinkedListItems>
  </Expand>
</Type>
```

O elemento `Size` faz referência ao comprimento da lista. `HeadPointer` aponta para o primeiro elemento, `NextPointer` refere-se ao próximo elemento e `ValueNode` refere-se ao valor do item.

O depurador avalia `NextPointer` `ValueNode` as expressões no `LinkedListItems` contexto do elemento nó, não o tipo de lista dos pais. No exemplo anterior, `CAtlList` `CNode` tem uma `atlcoll.h`classe (encontrada em ) que é um nó da lista vinculada. `m_pNext`e `m_element` são campos `CNode` dessa classe, `CAtlList` não da classe.

`ValueNode`pode ser deixado vazio, ou `this` `LinkedListItems` usar para se referir ao nó em si.

#### <a name="customlistitems-expansion"></a>Expansão de Itens de PersonalListIts

A `CustomListItems` expansão permite que você escreva lógica personalizada para atravessar uma estrutura de dados, como um hashtable. Use `CustomListItems` para visualizar estruturas de dados que podem usar expressões C++ para tudo o `ArrayItems` `IndexListItems`que `LinkedListItems`você precisa avaliar, mas não se encaixam no molde para , ou .

Você pode `Exec` usar para executar `CustomListItems` código dentro de uma expansão, usando as variáveis e objetos definidos na expansão. Você pode usar operadores lógicos, operadores aritméticos e operadores de atribuição com `Exec`. Você não pode `Exec` usar para avaliar funções, exceto para [funções intrínsecas de depurador](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) suportadas pelo avaliador de expressão C++.

O visualizador `CAtlMap` a seguir é `CustomListItems` um excelente exemplo onde é apropriado.

```xml
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>
    <Expand>
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">
        <Variable Name="iBucket" InitialValue="-1" />
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />
        <Variable Name="iBucketIncrement" InitialValue="-1" />

        <Size>m_nElements</Size>
        <Exec>pBucket = nullptr</Exec>
        <Loop>
          <If Condition="pBucket == nullptr">
            <Exec>iBucket++</Exec>
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>
            <Break Condition="iBucketIncrement == -1" />
            <Exec>iBucket += iBucketIncrement</Exec>
            <Exec>pBucket = m_ppBins[iBucket]</Exec>
          </If>
          <Item>pBucket,na</Item>
          <Exec>pBucket = pBucket->m_pNext</Exec>
        </Loop>
      </CustomListItems>
    </Expand>
</Type>
```

#### <a name="treeitems-expansion"></a><a name="BKMK_TreeItems_expansion"></a> Expansão de TreeItems
 Se o tipo visualizado representa uma árvore, o depurador pode percorrer a árvore e exibir seus filhos usando um nó `TreeItems`. Aqui está a visualização `std::map` para `TreeItems` o tipo usando um nó:

```xml
<Type Name="std::map&lt;*&gt;">
  <DisplayString>{{size = {_Mysize}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mysize</Item>
    <Item Name="[comp]">comp</Item>
    <TreeItems>
      <Size>_Mysize</Size>
      <HeadPointer>_Myhead->_Parent</HeadPointer>
      <LeftPointer>_Left</LeftPointer>
      <RightPointer>_Right</RightPointer>
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>
    </TreeItems>
  </Expand>
</Type>
```

A sintaxe é `LinkedListItems` semelhante ao nó. `LeftPointer`, `RightPointer`e `ValueNode` são avaliados sob o contexto da classe de nó de árvore. `ValueNode`pode ser deixado `this` vazio ou `TreeItems` usado para se referir ao nó em si.

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a> Expansão de ExpandedItem
 O `ExpandedItem` elemento gera uma visão infantil agregada, exibindo propriedades de classes básicas ou membros de dados como se fossem crianças do tipo visualizado. O depurador avalia a expressão especificada e anexa os nós da criança do resultado à lista infantil do tipo visualizado.

Por exemplo, o `auto_ptr<vector<int>>` tipo de ponteiro inteligente normalmente é exibido como:

 ![auto&#95;ptr&#60;vetor&#60;int&#62;&#62; expansão padrão](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Expansão padrão")

 Para ver os valores do vetor, você tem que detalhar `_Myptr` dois níveis na janela variável, passando pelo membro. Adicionando um elemento `ExpandedItem`, você pode eliminar a variável `_Myptr` da hierarquia e exibir diretamente os elementos do vetor:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![auto&#95;ptr&#60;vetor&#60;expansão int&#62;&#62; ExpandedItem](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "Expansão de ExpandedItem")

O exemplo a seguir mostra como agregar propriedades da classe base em uma classe derivada. Suponha que a classe `CPanel` seja derivada de `CFrameworkElement`. Em vez de repetir as propriedades `CFrameworkElement` que `ExpandedItem` vêm da classe base, a visualização `CPanel` do nó anexa essas propriedades à lista infantil da classe.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

O especificador de formato **nd**, que desativa a correspondência de visualização da classe derivada é necessário aqui. Caso contrário, `*(CFrameworkElement*)this` a expressão `CPanel` faria com que a visualização fosse aplicada novamente, pois as regras de correspondência do tipo de visualização padrão a consideram a mais adequada. Use o especificador de formato **nd** para instruir o depurador a usar a visualização da classe base ou a expansão padrão se a classe base não tiver visualização.

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a> Expansão de item sintético
 Enquanto o elemento `ExpandedItem` fornece uma exibição de dados mais simples eliminando as hierarquias, o nó `Synthetic` faz o oposto. Ele permite que você crie um elemento infantil artificial que não seja resultado de uma expressão. O elemento artificial pode ter elementos infantis próprios. No exemplo a seguir, a visualização do tipo `Concurrency::array` usa um nó de `Synthetic` para mostrar uma mensagem de diagnóstico para o usuário:

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>
    </Synthetic>
  </Expand>
</Type>
```

 ![Concorrência::Matriz com expansão de elementos sintéticos](../debugger/media/dbg_natvis_expand_synthetic.png "Concorrência::Matriz com expansão de elementos sintéticos")

### <a name="hresult-element"></a><a name="BKMK_HResult"></a>Elemento HResult
 O `HResult` elemento permite personalizar as informações mostradas para um **HRESULT** em janelas de depurador. O elemento `HRValue` deve conter o valor de 32 bits do **HRESULT** que deve ser personalizado. O `HRDescription` elemento contém as informações a serem exibidas na janela do depurador.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="uivisualizer-element"></a><a name="BKMK_UIVisualizer"></a>Elemento uivisualizer
Um elemento `UIVisualizer` registra um plug-in de visualizador gráfico no depurador. Um visualizador gráfico cria uma caixa de diálogo ou outra interface que mostra uma variável ou objeto de forma consistente com seu tipo de dados. O plug-in do visualizador deve ser de autoria de [VSPackage](../extensibility/internals/vspackages.md), e deve expor um serviço que o depurador pode consumir. O arquivo *.natvis* contém informações cadastrais para o plug-in, como seu nome, o GUID do serviço exposto e os tipos que ele pode visualizar.

Veja um exemplo de um elemento UIVisualizer:

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="1" MenuName="Vector Visualizer"/>
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="2" MenuName="List Visualizer"/>
.
.
</AutoVisualizer>
```

- `ServiceId`  -  Um `Id` par de `UIVisualizer`atributos identifica um . O `ServiceId` é o GUID do serviço que o pacote de visualizadores expõe. `Id`é um identificador único que diferencia os visualizadores, se um serviço fornece mais de um. No exemplo anterior, o mesmo serviço de visualizadores fornece dois visualizadores.

- O `MenuName` atributo define um nome visualizador para exibição no drop-down ao lado do ícone de lupa no depurador. Por exemplo:

  ![Menu de atalho do uivisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "Menu de atalho do uivisualizer")

Cada tipo definido no arquivo *.natvis* deve listar explicitamente quaisquer visualizadores de ida e primeira que possam exibi-lo. O depurador corresponde às referências do visualizador nas entradas do tipo com os visualizadores registrados. Por exemplo, a seguinte `std::vector` entrada `UIVisualizer` de tipo para referências no exemplo anterior.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 Você pode ver um `UIVisualizer` exemplo de a na extensão [Image Watch](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance) usado para exibir bitmaps na memória.

### <a name="customvisualizer-element"></a><a name="BKMK_CustomVisualizer"></a>Elemento personalvisualizador
 `CustomVisualizer`é um ponto de extensibilidade que especifica uma extensão VSIX que você escreve para controlar visualizações no código do Visual Studio. Para obter mais informações sobre como escrever extensões VSIX, consulte o [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

É muito mais trabalho para escrever um visualizador personalizado do que uma definição XML Natvis, mas você está livre de restrições sobre o que natvis faz ou não suporta. Os visualizadores personalizados têm acesso ao conjunto completo de APIs de extensibilidade de depurador, que podem consultar e modificar o processo de depuração ou se comunicar com outras partes do Visual Studio.

 Você pode `Condition`usar `IncludeView`os `ExcludeView` atributos e atributos em `CustomVisualizer` elementos.

 ## <a name="limitations"></a>Limitações

As personalizações natvis funcionam com classes e estruturas, mas não digitadas.

Natvis não suporta visualizadores para tipos primitivos (por exemplo, `int`) `bool`ou para ponteiros para tipos primitivos. Neste cenário, uma opção é usar o [especificador de formato](../debugger/format-specifiers-in-cpp.md) apropriado para o seu caso de uso. Por exemplo, se `double* mydoublearray` você usar em seu código, você poderá usar um especificador de formato `mydoublearray, [100]`de matriz na janela **relógio** do depurador, como a expressão , que mostra os primeiros 100 elementos.

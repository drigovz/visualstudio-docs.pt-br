---
title: Criar exibições personalizadas de objetos nativos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 63390672b246add079806c68a23b69f0e0132c2d
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850199"
---
# <a name="create-custom-views-of-native-objects"></a>Criar exibições personalizadas de objetos nativos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A estrutura de Natvis do Visual Studio permite que você personalize a maneira como o Visual Studio exibe tipos nativos em janelas de variáveis do depurador (por exemplo, as janelas de **inspeção**, **locais**e **dicas de dados** .  

 O Natvis substitui o arquivo **autoexp. dat** que foi usado em versões anteriores do Visual Studio e oferece sintaxe XML, melhor diagnóstico, controle de versão e suporte a vários arquivos.  

> [!NOTE]
> Você não pode usar a estrutura Natvis para visualizações quando:  
> 
> - Você está depurando um projeto de área de trabalho do Windows com o C++ tipo de depurador definido como **Misto**.  
>   - Você está fazendo uma depuração de modo misto em um aplicativo de área de trabalho do Windows no modo de compatibilidade gerenciado (**ferramentas/opções/depuração/geral/usar modo de compatibilidade gerenciado**).  
>   - Você está depurando em um aplicativo de área de trabalho do Windows no modo de compatibilidade nativa (**ferramentas/opções/depuração/geral/usar modo de compatibilidade nativo**).  

## <a name="BKMK_Why_create_visualizations_"></a>Por que criar visualizações de Natvis?  
 Você pode usar a estrutura Natvis para criar regras de visualização para os tipos criados para que os desenvolvedores possam vê-las facilmente durante a depuração.  

 Por exemplo, a imagem abaixo mostra uma variável do tipo [Windows:: UI:: XAML:: Controls:: TextBox](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textbox.aspx) que é exibido no depurador sem nenhuma visualização personalizada aplicada.  

 ![Visualização padrão da caixa de texto](../debugger/media/dbg-natvis-textbox-default.png "DBG_NATVIS_TextBox_Default")  

 A linha realçada mostra a propriedade `Text` da classe `TextBox`. A hierarquia de classe complexa dificulta a localização desse valor; Além disso, o depurador não sabe como interpretar o tipo de cadeia de caracteres personalizada usado pelo objeto, portanto, você não pode ver a cadeia de caracteres mantida dentro da caixa de texto.  

 A mesma `TextBox` parece muito mais simples na janela variável quando regras de visualização personalizadas são aplicadas. Os membros importantes da classe podem ser exibidos juntos e o depurador mostra o valor da cadeia de caracteres subjacente do tipo de cadeia de caracteres personalizada.  

 ![Dados de caixa de texto usando o visualizador](../debugger/media/dbg-natvis-textbox-visualizer.png "DBG_NATVIS_TextBox_Visualizer")  

## <a name="BKMK_Using_Natvis_files"></a>Usando arquivos Natvis  
 os arquivos. natvis são arquivos XML com uma extensão. natvis. O esquema é definido em **%VSINSTALLDIR%\Xml\Schemas\natvis.xsd**.  

 A estrutura básica de um arquivo. natvis é um ou mais elementos `Type`, em que cada elemento `Type` representa uma entrada de visualização para um tipo cujo nome totalmente qualificado é especificado no atributo `Name`.  

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

 O Visual Studio fornece alguns arquivos. natvis na pasta **%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers** . Esses arquivos contêm regras de visualização para muitos tipos comuns e podem servir como exemplos quando você está escrevendo visualizações para novos tipos.  

## <a name="adding-natvis-files-to-your-projects"></a>Adicionando arquivos. natvis a seus projetos  
 Você pode adicionar arquivos. natvis a qualquer C++ projeto.  

 Para adicionar um novo arquivo. natvis, com um projeto C++ aberto, selecione o nó do projeto na **Gerenciador de soluções**e clique em **Adicionar/novo item/Visual C++ /utilitário de visualização do depurador (. natvis)** . O depurador carregará automaticamente os arquivos C++ de Natvis de projetos. Por padrão, os arquivos Natvis em seu projeto também são inseridos no arquivo. pdb compilado pelo projeto. Isso significa que, se você depurar o binário criado por esse projeto, o depurador carregará o arquivo Natvis do. pdb mesmo que você não tenha o projeto aberto. Se você não quiser que o arquivo. natvis seja incluído no. pdb, clique com o botão direito do mouse no arquivo. natvis na **Gerenciador de soluções**e, na janela **Propriedades de configuração** , defina **excluído de Compilar** para **Sim**.  

 É recomendável que você edite arquivos Natvis usando o Visual Studio quaisquer alterações feitas durante a depuração entrarem em vigor automaticamente quando você salvar o arquivo. Você também obtém uma experiência de edição aprimorada do IntelliSense.  

 Os arquivos Natvis que são carregados de um. pdb aplicam-se somente aos tipos no módulo ao qual o PDB se refere. Por exemplo, se Module1. pdb definir uma entrada para um tipo chamado `Test`, essa entrada será aplicada somente à classe de **teste** no Module1. dll. Se outro módulo também definir uma classe chamada **Test**, a entrada natvis do Module1. pdb não se aplicará a ela.  

## <a name="BKMK_natvis_location"></a>Implantando arquivos. natvis  
 Se seu arquivo. natvis se aplicar somente aos tipos que você está criando em um projeto do Visual Studio, você não precisará fazer nada; o. natvis está incluído no. pdb. Você pode, no entanto, adicionar arquivos. natvis ao seu diretório de usuário ou a um diretório do sistema se quiser que eles se apliquem a vários projetos.  

 A ordem na qual os arquivos. natvis são avaliados é a seguinte:  

1. arquivos. natvis inseridos em um. pdb que você está Depurando (a menos que exista um arquivo com o mesmo nome em um projeto carregado)  

2. arquivos. natvis que fazem parte de um projeto C++ carregado ou um item de solução de nível superior. Isso inclui todos os C++ projetos carregados, incluindo bibliotecas de classes, mas não inclui projetos de outras linguagens (por exemplo, você não pode carregar um arquivo. C# natvis de um projeto). Para projetos executáveis, você deve usar os itens da solução para hospedar qualquer arquivo. natvis que ainda não esteja presente em um. pdb, já que C++ não há nenhum projeto disponível.  

3. O diretório natvis específico do usuário ( **%USERPROFILE%\My Documentos\visual Studio 2015 \ Visualizers**  

4. O diretório Natvis de todo o sistema ( **%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers**). É aí que os arquivos. natvis instalados com o Visual Studio são copiados. Você também pode adicionar outros arquivos a esse diretório se tiver permissões de administrador.  

## <a name="modifying-natvis-files-while-debugging"></a>Modificando arquivos. natvis durante a depuração  
 Você pode modificar um arquivo. natvis no IDE enquanto estiver depurando o projeto no qual ele está incluído. Abra o arquivo no IDE (usando a mesma instância do Visual Studio com a qual você está depurando), modifique-o e salve-o. Assim que o arquivo é salvo, as janelas de **inspeção** e **locais** devem ser atualizadas para refletir a alteração. Se você modificar o arquivo. natvis fora do IDE, as alterações não entrarão em vigor automaticamente. Para atualizar as janelas, você pode avaliar o comando **. natvisreload** na janela **Watch** . Isso faz com que as alterações entrem em vigor sem reiniciar a sessão de depuração.  

 Você também pode adicionar ou excluir arquivos. natvis para uma solução que você está Depurando, e o Visual Studio adicionará ou removerá as visualizações relevantes.  

 Você não pode modificar um arquivo. natvis enquanto estiver Depurando se ele estiver inserido em um. pdb.  

 Use o comando **. natvisreload** quando estiver atualizando o arquivo natvis para uma versão mais recente (por exemplo, se ele tiver sido verificado no controle do código-fonte e se você quiser selecionar alterações recentes que outra pessoa fez no arquivo). É recomendável que você edite arquivos natvis usando o editor de XML do Visual Studio.  

## <a name="BKMK_Expressions_and_formatting"></a> Expressões e formatação  
 As visualizações do Natvis usam expressões do C++ para especificar os itens de dados a serem exibidos. Além dos aprimoramentos e limitações das C++ expressões no depurador que são descritas no operador de [contexto (C++)](../debugger/context-operator-cpp.md), você deve estar ciente das seguintes diferenças:  

- As expressões do Natvis são avaliadas no contexto do objeto que está sendo visualizado, não do registro de ativação atual. Por exemplo, se você usar `x` em uma expressão Natvis, isso se refere ao campo chamado `x` no objeto que está sendo visualizado, não a uma variável local chamada `x` na função que está sendo executada no momento. Você não pode acessar variáveis locais em expressões Natvis, embora possa acessar variáveis globais.  

- As expressões do natvis não permitem avaliação ou efeitos colaterais de função. Isso significa que as chamadas de função e os operadores de atribuição são ignorados. Como as [funções intrínsecas do depurador](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) não têm efeitos colaterais, elas podem ser livremente chamadas de qualquer expressão do natvis, mesmo que outras chamadas de função estejam desabilitadas.  

  Para controlar como uma expressão é exibida em uma janela variável, você pode usar qualquer um dos especificadores de formato descritos na seção [formatos de especificadores](../debugger/format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers) dos [especificadores de C++ formato no](../debugger/format-specifiers-in-cpp.md) tópico. Observe que os especificadores de formato são ignorados quando a entrada de virtualização é usada internamente pelo Natvis, como a expressão de `Size` em uma expansão ArrayItems.  

## <a name="natvis-views"></a>Exibições de Natvis  
 As exibições de Natvis permitem que você veja qualquer tipo de mais de uma maneira. Por exemplo, você pode definir uma exibição denominada **Simple** que fornece uma exibição simplificada de um tipo. Por exemplo, aqui está a visualização de `std::vector`:  

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

 Os elementos `DisplayString` e `ArrayItems` são usados na exibição padrão e na exibição simples, enquanto os itens `[size]` e `[capacity]` são excluídos da exibição simples. Você pode usar o especificador de formato de **exibição** para especificar uma exibição alternativa. Na janela **Watch** , você especifica a exibição simples como **VEC, View (simples)** :  

 ![janela Inspeção com exibição simples](../debugger/media/watch-simpleview.png "Watch-SimpleView")  

## <a name="BKMK_Diagnosing_Natvis_errors"></a>Diagnosticando erros de Natvis  
 Você pode usar o diagnóstico de Natvis para solucionar erros de sintaxe e análise. Quando o depurador encontra erros em uma entrada de visualização, ele ignora os erros e exibe o tipo em sua forma bruta ou escolhe outra visualização adequada. Para entender por que uma determinada entrada de visualização é ignorada e ver quais são os erros subjacentes, você pode ativar a opção ferramentas de diagnóstico de Natvis **/Opções/depuração/janela de saídaC++ /mensagens de diagnóstico de natvis (somente)** . Os erros são exibidos na janela **saída** .  

## <a name="BKMK_Syntax_reference"></a>Referência de sintaxe de Natvis  

### <a name="BKMK_AutoVisualizer"></a> Elemento AutoVisualizer  
 O elemento `AutoVisualizer` é o nó raiz do arquivo. natvis e contém o atributo `xmlns:` namespace.  

```xml  
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
.  
.  
</AutoVisualizer>  
```  

### <a name="BKMK_Type"></a> Elemento Type  
 Um tipo básico tem esta aparência:  

```xml  
<Type Name="[fully qualified type name]">  
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>  
  <Expand>  
    ...  
  </Expand>  
</Type>  

```  

 Ele especifica:  

1. Para qual tipo essa visualização deve ser usada (atributo `Type Name`).  

2. Qual deve ser a aparência de um objeto desse tipo (semelhante à do elemento `DisplayString`).  

3. Como deve ser a aparência dos membros do tipo quando o usuário o expande em uma janela variável (o nó `Expand`).  

   **Classes de modelo** O atributo `Name` do elemento `Type` aceita um asterisco `*` como um caractere curinga que pode ser usado para nomes de classe de modelo:  

```xml  
<Type Name="ATL::CAtlArray&lt;*&gt;">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  

```  

 Neste exemplo, a mesma visualização será usada caso o objeto seja um `CAtlArray<int>` ou um `CAtlArray<float>`. Se houver uma entrada de visualização específica para um `CAtlArray<float>`, ela terá precedência sobre a genérica.  

 Observe que os parâmetros do modelo podem ser referenciados na entrada de visualização usando as macros $T1, $T2 e assim por diante. Para localizar exemplos dessas macros, consulte os arquivos .natvis que acompanham o Visual Studio.  

#### <a name="BKMK_Visualizer_type_matching"></a> Correspondência de tipo de visualizador  
 Se uma entrada de visualização não for validada, a próxima visualização disponível será usada.  

#### <a name="inheritable-attribute"></a>Atributo herdável  
 Você pode especificar se uma visualização se aplica somente a um tipo base ou a um tipo base e a todos os tipos derivados com o atributo opcional `Inheritable`. No seguinte, a visualização aplica-se somente ao tipo de `BaseClass`:  

```xml  
<Type Name="Namespace::BaseClass" Inheritable="true">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

 O valor padrão de `Inheritable` é `true`.  

#### <a name="priority-attribute"></a>Atributo de prioridade  
 O atributo `Priority` especifica a ordem na qual as definições alternativas serão usadas se uma definição não for analisada. Os valores possíveis de `Priority` são: `Low`, `MediumLow`,`Medium`, `MediumHigh`e `High`, e o valor padrão é `Medium`.  

 O atributo Priority só deve ser usado para distinguir entre as prioridades no mesmo arquivo. natvis, não entre arquivos diferentes.  

 No exemplo a seguir, analisaremos primeiro a entrada que corresponde à STL 2015 e, se isso não for analisado, usaremos a entrada alternativa para a versão 2013 da STL:  

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

#### <a name="BKMK_Versioning"></a>Elemento Version  
 Use o elemento `Version` para definir o escopo de visualizações para módulos específicos e suas versões de modo que seja possível minimizar conflitos de nome e usar visualizações diferentes para versões diferentes de tipos. Por exemplo:  

```xml  
<Type Name="DirectUI::Border">  
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>  
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>  
  <Expand>  
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>  
  </Expand>  
</Type>  
```  

 Neste exemplo, a visualização é aplicável somente para o tipo de `DirectUI::Border` encontrado na `Windows.UI.Xaml.dll` da versão 1,0 a 1,5. Observe que a adição de elementos de versão escopou a entrada de visualização para um módulo e versão específicos e reduz incompatibilidades involuntárias, mas se um tipo for definido em um arquivo de cabeçalho comum usado por diferentes módulos, a visualização com controle de versão não será aplicada quando o tipo não está no módulo especificado.  

#### <a name="optional-attribute"></a>Atributo opcional  
 O atributo `Optional` pode aparecer em qualquer nó. Se qualquer subexpressão dentro de um nó opcional falhar ao analisar, esse nó será ignorado, mas o restante do elemento Type ainda será válido. No tipo a seguir, `[State]` é não opcional, mas `[Exception]` é opcional.  Isso significa que, se `MyNamespace::MyClass` contiver um campo chamado _`M_exceptionHolder`, você ainda `[State]` nó e o nó de `[Exception]`, mas se o `_M_exceptionHolder` estiver ausente, você verá apenas o nó de `[State]`.  

```xml  
<Type Name="MyNamespace::MyClass">  
    <Expand>  
      <Item Name="[State]">_M_State</Item>  
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>  
    </Expand>  
</Type>  
```  

### <a name="BKMK_Condition_attribute"></a> Atributo de condição  
 O atributo opcional `Condition` está disponível para muitos elementos de visualização e especifica quando uma regra de visualização deve ser usada. Se a expressão dentro do atributo Condition for resolvida como `false`, a regra de visualização especificada pelo elemento não será aplicada. Se ele for avaliado como true ou se não houver nenhum atributo `Condition`, a regra de visualização será aplicada ao tipo. Você pode usar esse atributo para `if-else` lógica nas entradas de visualização. Por exemplo, a visualização abaixo tem dois elementos `DisplayString` para um tipo de ponteiro inteligente:  

```xml  
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  

```  

 Quando o membro `_Myptr` é `null`, a condição do primeiro elemento `DisplayString` é resolvida como `true`, para que o formulário seja exibido. Quando o membro `_Myptr` não é `null`, a condição é avaliada como `false`e o segundo elemento `DisplayString` é exibido.  

### <a name="includeview-and-excludeview-attributes"></a>Atributos IncludeView e ExcludeView  
 Esses atributos especificam os elementos que devem ser exibidos ou não exibidos em modos de exibição diferentes. Por exemplo, dada a especificação de Natvis do `std::vector`:  

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

 A exibição simples não exibe os itens [tamanho] e [capacidade] na exibição simples. Se tivéssemos usado `IncludeView="simple"` em vez de `ExcludeView`, os itens `[size]` e `[capacity]` seriam mostrados na exibição simples em vez de na exibição padrão.  

 Você pode usar os atributos `IncludeView` e `ExcludeView` em tipos, bem como em membros individuais.  

### <a name="BKMK_DisplayString"></a>DisplayString  
 Um elemento `DisplayString` especifica a cadeia de caracteres a ser exibida como o valor da variável. Aceita cadeias de caracteres arbitrárias misturadas a expressões. Tudo dentro das chaves é interpretado como uma expressão. Por exemplo, uma entrada `DisplayString` como esta:  

```xml  
<Type Name="CPoint">  
  <DisplayString>{{x={x} y={y}}}</DisplayString>   
</Type>  

```  

 Significa que as variáveis do tipo `CPoint` são exibidas da seguinte maneira:  

 ![Usando um elemento DisplayString](../debugger/media/dbg-natvis-cpoint-displaystring.png "DBG_NATVIS_CPoint_DisplayString")  

 Na expressão `DisplayString`, `x` e `y`, que são membros de `CPoint`, estão entre chaves e, portanto, seus valores são avaliados. A expressão também mostra como você pode escapar uma chave usando chaves duplas (`{{` ou `}}`).  

> [!NOTE]
> O elemento `DisplayString` é o único elemento que aceita cadeias de caracteres arbitrárias e a sintaxe de chaves. Todos os outros elementos de visualização aceitam apenas expressões avaliadas pelo depurador.  

### <a name="BKMK_StringView"></a>StringView  
 O elemento `StringView` define a expressão cujo valor será enviado ao visualizador interno de texto. Por exemplo, suponha que temos a seguinte visualização para o tipo `ATL::CStringT`:  

```xml  
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
</Type>  

```  

 O objeto `CStringT` é parecido com:  

 ![Elemento CStringT DisplayString](../debugger/media/dbg-natvis-displaystring-cstringt.png "DBG_NATVIS_DisplayString_CStringT")  

 A visualização exibe um objeto `CStringT` em uma janela variável como esta:  

 A adição de um elemento `StringView` indica para o depurador que esse valor pode ser exibido por uma visualização de texto:  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
  <StringView>m_pszData,su</StringView>  
</Type>  
```  

 Observe o ícone de lupa mostrado ao lado do valor abaixo. A escolha do ícone inicia o visualizador de texto que exibe a cadeia de caracteres para a qual `m_pszData` aponta.  

 ![Dados do CStringT com o Visualizador do StringView](../debugger/media/dbg-natvis-stringview-cstringt.png "DBG_NATVIS_StringView_CStringT")  

> [!NOTE]
> Observe que a expressão `{m_pszData,su}` inclui um C++ especificador de formato `su` para exibir o valor como uma cadeia de caracteres Unicode. Consulte os [especificadores de C++ formato em](../debugger/format-specifiers-in-cpp.md) para obter mais informações.  

### <a name="BKMK_Expand"></a>Expanda  
 O nó `Expand` é usado para personalizar os filhos do tipo visualizado quando o usuário o expandir nas janelas variáveis. Aceita uma lista de nós filhos que definem os elementos filhos.  

 O nó `Expand` é opcional.  

- Se um nó `Expand` não é especificado em uma entrada de visualização, as regras padrão de expansão do Visual Studio são usadas.  

- Se um nó `Expand` for especificado sem nós filhos abaixo dele, o tipo não será expansível nas janelas do depurador.  

#### <a name="BKMK_Item_expansion"></a> Expansão de item  
 O elemento `Item` é o elemento mais básico e mais comum para ser usado em um nó `Expand`. `Item` define um único elemento filho. Por exemplo, suponha que você tenha uma classe `CRect` com `top`, `left`, `right` e `bottom` como campos e a seguinte entrada de visualização:  

```xml  
<Type Name="CRect">  
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>  
  <Expand>  
    <Item Name="Width">right - left</Item>  
    <Item Name="Height">bottom - top</Item>  
  </Expand>  
</Type>  

```  

 O tipo de `CRect` terá a seguinte aparência:  

 ![CRect com expansão de elemento de item](../debugger/media/dbg-natvis-expand-item-crect1.png "DBG_NATVIS_Expand_Item_CRect1")  

 As expressões especificadas nos elementos `Width` e `Height` são avaliadas e mostradas na coluna de valor. O nó `[Raw View]` é criado automaticamente pelo depurador sempre que uma expansão personalizada é usada. Ele é expandido na captura de tela acima para mostrar como a exibição bruta do objeto é diferente da visualização. A expansão padrão do Visual Studio cria uma subárvore para a classe base e lista todos os membros de dados da classe base como filhos.  

> [!NOTE]
> Se a expressão do elemento item apontar para um tipo complexo, o `Item` nó em si será expansível.  

#### <a name="BKMK_ArrayItems_expansion"></a> Expansão de ArrayItems  
 Use o nó `ArrayItems` para que o depurador do Visual Studio interprete o tipo como uma matriz e exiba seus elementos individuais. A visualização para `std::vector` é um bom exemplo:  

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

 ![std:: vector usando a expansão ArrayItems](../debugger/media/dbg-natvis-expand-arrayitems-stdvector.png "DBG_NATVIS_Expand_ArrayItems_StdVector")  

 No mínimo, o nó `ArrayItems` deve ter:  

1. Uma expressão `Size` (que deve ser avaliada como um inteiro) para que o depurador entenda o comprimento da matriz  

2. Uma expressão `ValuePointer` que deve apontar para o primeiro elemento (que deve ser um ponteiro de um tipo de elemento que não seja `void*`).  

   O valor padrão do limite inferior da matriz é 0. O valor pode ser substituído usando um elemento `LowerBound` (exemplos podem ser encontrados nos arquivos .natvis que acompanham o Visual Studio).  

   Agora você pode usar o operador de `[]` com uma expansão de `ArrayItems`, por exemplo `vector[i]`. O operador [] pode ser usado com qualquer visualização de uma matriz unidimensional que usa `ArrayItems` ou `IndexListItems`, mesmo que o próprio tipo não permita esse operador (por exemplo `CATLArray`).  

   Matrizes de várias dimensões também podem ser especificadas. O depurador precisa apenas de um pouco mais de informações para exibir corretamente os elementos filho nesse caso:  

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

 `Direction` especifica se a matriz é uma ordem de linha principal ou de coluna principal. `Rank` especifica a classificação da matriz. O elemento `Size` aceita o parâmetro implícito `$i` que ele substitui pelo índice de dimensão para descobrir o tamanho da matriz na dimensão. Por exemplo, no exemplo anterior, a expressão `_M_extent.M_base[0]` deve fornecer o comprimento da dimensão 0, `_M_extent._M_base[1]` da primeira e sucessivamente.  

 Veja qual é a aparência de um objeto `Concurrency::array` bidimensional no depurador:  

 ![Matriz dimensional dupla com expansão ArrayItems](../debugger/media/dbg-natvis-expand-arrayitems-2d.png "DBG_NATVIS_Expand_ArrayItems_2D")  

#### <a name="BKMK_IndexListItems_expansion"></a> Expansão de IndexListItems  
 Você pode usar a expansão de `ArrayItems`, somente se os elementos da matriz estiverem dispostos de forma contígua na memória. O depurador chega ao elemento seguinte incrementando o elemento atual com o ponteiro. Para dar suporte aos casos nos quais você precisa manipular o índice do nó de valor, os nós `IndexListItems` podem ser usados. Esta é uma visualização que usa o nó `IndexListItems`:  

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

 Agora você pode usar o operador de `[]` com uma expansão de `IndexListItems`, por exemplo `vector[i]`. O operador `[]` pode ser usado com qualquer visualização de uma matriz unidimensional que usa `ArrayItems` ou `IndexListItems`, mesmo que o próprio tipo não permita esse operador (por exemplo `CATLArray`).  

 A única diferença entre `ArrayItems` e `IndexListItems` é que o `ValueNode` espera a expressão completa para<sup>o elemento i</sup> com o parâmetro de `$i` implícito.  

#### <a name="BKMK_LinkedListItems_expansion"></a> Expansão de LinkedListItems  
 Se o tipo visualizado representa uma lista vinculada, o depurador pode exibir seus filhos usando um nó `LinkedListItems`. Veja a visualização do tipo `CAtlList` usando esse recurso:  

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

- As expressões `NextPointer` e `ValueNode` são avaliadas no contexto do elemento do nó da lista vinculada e não do tipo da lista pai. No exemplo anterior, `CAtlList` tem uma classe `CNode` (encontrada em `atlcoll.h`) que representa um nó da lista vinculada. `m_pNext` e `m_element` são campos dessa classe `CNode` e não da classe `CAtlList`.  

- O `ValueNode` pode ser deixado em branco ou pode conter `this` para fazer referência ao nó da lista vinculada.  

#### <a name="customlistitems-expansion"></a>Expansão de CustomListItems  
 A expansão de `CustomListItems` permite que você escreva uma lógica personalizada para percorrer uma estrutura de dados, como uma tabela de hash. Você deve usar `CustomListItems` para visualizar estruturas de dados nas quais tudo o que você precisa avaliar é C++ expresso por meio de expressões, mas não se ajusta perfeitamente ao molde para `ArrayItems`, `TreeItems`ou `LinkedListItems.`  

 O visualizador para CAtlMap é um excelente exemplo de onde `CustomListItems` é apropriado.  

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

#### <a name="BKMK_TreeItems_expansion"></a> Expansão de TreeItems  
 Se o tipo visualizado representa uma árvore, o depurador pode percorrer a árvore e exibir seus filhos usando um nó `TreeItems`. Veja a visualização do tipo `std::map` usando esse recurso:  

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

 A sintaxe é muito semelhante ao nó `LinkedListItems`. `LeftPointer`, `RightPointer`e `ValueNode` são avaliados sob o contexto da classe de nó de árvore e `ValueNode` podem ser deixados vazios ou ter `this` para se referir ao nó de árvore em si.  

#### <a name="BKMK_ExpandedItem_expansion"></a> Expansão de ExpandedItem  
 O elemento `ExpandedItem` pode ser usado para gerar uma exibição filho agregada exibindo propriedades de classes base ou de membros de dados como se fossem filhos do tipo visualizado. A expressão especificada é avaliada e os nós filhos do resultado são acrescentados à lista filho do tipo visualizado. Por exemplo, suponha que temos um tipo de ponteiro inteligente `auto_ptr<vector<int>>` que será normalmente exibido como:  

 ![expansão&#95;&#62; padrão&#60;de&#60;vetor&#62; de auto PTR](../debugger/media/dbg-natvis-expand-expandeditem-default.png "DBG_NATVIS_Expand_ExpandedItem_Default")  

 Para ver os valores do vetor, faça uma pesquisa detalhada de dois níveis na janela variável que passa pelo membro _Myptr. Adicionando um elemento `ExpandedItem`, você pode eliminar a variável `_Myptr` da hierarquia e exibir diretamente o vetor elements::  

```xml  
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  

```  

 ![expansão&#95;de&#60;ExpandedItem&#60;de&#62; &#62; vetor int de auto PTR](../debugger/media/dbg-natvis-expand-expandeditem-visualized.png "DBG_NATVIS_Expand_ExpandedItem_Visualized")  

 O exemplo a seguir mostra como agregar propriedades da classe base em uma classe derivada. Suponha que a classe `CPanel` seja derivada de `CFrameworkElement`. Em vez de repetir as propriedades provenientes da classe base `CFrameworkElement`, o nó `ExpandedItem` permite que essas propriedades sejam acrescentadas à lista filho da classe `CPanel`. O especificador de formato **ND** que desativa a correspondência de visualização para a classe derivada é necessário aqui. Caso contrário, a expressão `*(CFrameworkElement*)this` fará com que a visualização `CPanel` seja aplicada novamente porque o tipo de visualização padrão correspondente às regras a considera mais apropriada. O uso do especificador de formato **ND** instrui o depurador a usar a visualização da classe base ou a expansão padrão da classe base se a classe base não tiver uma visualização.  

```xml  
<Type Name="CPanel">  
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>  
  <Expand>  
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>  
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>  
  </Expand>  
</Type>  

```  

#### <a name="BKMK_Synthetic_Item_expansion"></a>Expansão de item sintético  
 Enquanto o elemento `ExpandedItem` fornece uma exibição de dados mais simples eliminando as hierarquias, o nó `Synthetic` faz o oposto. Ele permite que você crie um elemento filho artificial (ou seja, um elemento filho que não seja um resultado de uma expressão). Esse elemento filho pode conter seus próprios elementos filhos. No exemplo a seguir, a visualização do tipo `Concurrency::array` usa um nó de `Synthetic` para mostrar uma mensagem de diagnóstico para o usuário:  

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

 ![Concurrency:: array com o elemento sythentic expansio](../debugger/media/dbg-natvis-expand-synthetic.png "DBG_NATVIS_Expand_Synthetic")  

### <a name="BKMK_HResult"></a>Resultado  
 O elemento `HResult` permite que você personalize as informações que são exibidas para um HRESULT em janelas do depurador. O elemento `HRValue` deve conter o valor de 32 bits do HRESULT que deve ser personalizado. O elemento `HRDescription` contém as informações que são exibidas no depurador.  

```  

<HResult Name="MY_E_COLLECTION_NOELEMENTS">  
  <HRValue>0xABC0123</HRValue>  
  <HRDescription>No elements in the collection.</HRDescription>  
</HResult>  
```  

### <a name="BKMK_UIVisualizer"></a>UIVisualizer  
 Um elemento `UIVisualizer` registra um plug-in de visualizador gráfico no depurador. Um plug-in de visualizador gráfico cria uma caixa de diálogo ou outra interface para exibir uma variável ou um objeto de maneira apropriada para o tipo de dados. O plug-in do visualizador deve ser criado como um [VSPackage](../extensibility/internals/vspackages.md) e precisa expor um serviço que pode ser consumido pelo depurador. O arquivo .natvis contém informações de registro para o plug-in, como o nome, a GUID do serviço exposto e também os tipos que ele pode visualizar.  

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

 Um `UIVisualizer` é identificado por um `ServiceId` - par de atributos `Id`. `ServiceId` é o GUID do serviço exposto pelo pacote do visualizador, `Id` é um identificador exclusivo que pode ser usado para diferenciar os visualizadores se um serviço fornecer mais de um visualizador. No exemplo anterior, o mesmo serviço de visualizador fornece dois visualizadores.  

 O atributo `MenuName` é o que os usuários veem como sendo o nome do visualizador quando abrem o menu suspenso ao lado do ícone de lupa nas janelas variáveis do depurador, por exemplo:  

 ![Menu de atalho do menu UIVisualizer](../debugger/media/dbg-natvis-vectorvisualizer.png "DBG_NATVIS_VectorVisualizer")  

 Cada tipo definido no arquivo .natvis deve listar explicitamente os visualizadores de interface de usuário que podem exibi-los. O depurador corresponde as referências do visualizador nas entradas de tipo para corresponder os tipos aos visualizadores registrados. Por exemplo, a seguinte entrada de tipo para `std::vector` faz referência a UIVisualizer no exemplo anterior.  

```xml
<Type Name="std::vector&lt;int,*&gt;">  
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />  
</Type>  
```  

 Você pode ver um exemplo de UIVisualizer na extensão de inspeção de imagem usada para exibir bitmaps na memória: [ImageWatch](https://visualstudiogallery.msdn.microsoft.com/e682d542-7ef3-402c-b857-bbfba714f78d)  

### <a name="customvisualizer-element"></a>Elemento CustomVisualizer  
 `CustomVisualizer` é um ponto de extensibilidade que especifica uma extensão VSIX que você pode escrever para controlar a visualização no código executado no Visual Studio. Para obter mais informações sobre como escrever extensões VSIX, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Escrever um visualizador personalizado é muito mais trabalho do que escrever uma definição de natvis XML, mas você está livre de restrições sobre o que o natvis dá suporte ou não dá suporte a. Visualizadores personalizados têm acesso ao conjunto completo de APIs de extensibilidade do depurador, que podem ser usados para consultar e modificar o processo de depuração ou se comunicar com outras partes do Visual Studio.  

 Você pode usar os atributos `Condition`, `IncludeView`e `ExcludeView` nos elementos CustomVisualizer.

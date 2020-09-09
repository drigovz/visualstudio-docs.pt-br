---
title: Técnicas de depuração do MFC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- AfxEnableMemoryTracking
- CMemoryState
- delayFreeMemDF
- checkAlwaysMemDF
- vs.debug.mfc
- vs.debug.objects.dump
- vs.debug.memory.dump
- allocMemDF
- afxMemDF
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [MFC]
ms.assetid: b154fc31-5e90-4734-8cbd-58dd9fe1f750
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06b42dbf31a8b5f4cb66de047bc1e08a4f840353
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600234"
---
# <a name="mfc-debugging-techniques"></a>Técnicas de depuração MFC
Se você estiver depurando um programa MFC, essas técnicas de depuração poderão ser úteis.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Neste tópico
[AfxDebugBreak](#BKMK_AfxDebugBreak)

[A macro de rastreamento](#BKMK_The_TRACE_macro)

[Detectando vazamentos de memória no MFC](#BKMK_Memory_leak_detection_in_MFC)

- [Acompanhamento de alocações de memória](#BKMK_Tracking_memory_allocations)

- [Habilitando o diagnóstico de memória](#BKMK_Enabling_memory_diagnostics)

- [Tirando instantâneos de memória](#BKMK_Taking_memory_snapshots)

- [Exibindo estatísticas de memória](#BKMK_Viewing_memory_statistics)

- [Obtendo despejos de objeto](#BKMK_Taking_object_dumps)

  - [Interpretando despejos de memória](#BKMK_Interpreting_memory_dumps)

  - [Personalizando despejos de objeto](#BKMK_Customizing_object_dumps)

  - [Reduzindo o tamanho de uma compilação de depuração do MFC](#BKMK_Reducing_the_size_of_an_MFC_Debug_build)

  - [Criando um aplicativo MFC com informações de depuração para os módulos selecionados](#BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules)

## <a name="afxdebugbreak"></a><a name="BKMK_AfxDebugBreak"></a> AfxDebugBreak
O MFC fornece uma função [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) especial para evitar a codificação de pontos de interrupção no código-fonte:

```cpp
AfxDebugBreak( );
```

Em plataformas Intel, o `AfxDebugBreak` produz o código a seguir, que é interrompido no código-fonte em vez de no código kernel:

```cpp
_asm int 3
```

Em outras plataformas, o `AfxDebugBreak` simplesmente chama o `DebugBreak`.

Não se esqueça de remover as instruções `AfxDebugBreak` ao criar uma compilação da versão ou usar as `#ifdef _DEBUG` para delimitá-los.

[Neste tópico](#BKMK_In_this_topic)

## <a name="the-trace-macro"></a><a name="BKMK_The_TRACE_macro"></a> A macro TRACE
Para exibir mensagens do seu programa no depurador [janela de Saída](../ide/reference/output-window.md), você pode usar a macro [ATLTRACE](/previous-versions/6xkxyz08(v=vs.140)) ou a macro [TRACE](/previous-versions/6w95a4ha(v=vs.140)) do MFC. Assim como as [asserções](../debugger/c-cpp-assertions.md), as macros de rastreamento estão ativas somente na versão de depuração do programa e desaparecem quando compiladas na versão de lançamento.

Os exemplos a seguir mostram algumas das formas que você pode usar a macro **TRACE**. Como o `printf`, a macro **TRACE** pode lidar com um número de argumentos.

```cpp
int x = 1;
int y = 16;
float z = 32.0;
TRACE( "This is a TRACE statement\n" );

TRACE( "The value of x is %d\n", x );

TRACE( "x = %d and y = %d\n", x, y );

TRACE( "x = %d and y = %x and z = %f\n", x, y, z );
```

A macro de rastreamento manipula adequadamente os \* parâmetros char e wchar_t \* . Os exemplos a seguir demonstram o uso da macro TRACE junto com os diferentes tipos de parâmetros de cadeia de caracteres.

```cpp
TRACE( "This is a test of the TRACE macro that uses an ANSI string: %s %d\n", "The number is:", 2);

TRACE( L"This is a test of the TRACE macro that uses a UNICODE string: %s %d\n", L"The number is:", 2);

TRACE( _T("This is a test of the TRACE macro that uses a TCHAR string: %s %d\n"), _T("The number is:"), 2);
```

Para obter mais informações sobre a macro **TRACE**, confira [Serviços de diagnóstico](/cpp/mfc/reference/diagnostic-services).

[Neste tópico](#BKMK_In_this_topic)

## <a name="detecting-memory-leaks-in-mfc"></a><a name="BKMK_Memory_leak_detection_in_MFC"></a> Detectando vazamentos de memória no MFC
O MFC fornece classes e funções para detectar a memória alocada, mas nunca desalocada.

### <a name="tracking-memory-allocations"></a><a name="BKMK_Tracking_memory_allocations"></a> Acompanhando alocações de memória
No MFC, você pode usar a macro [DEBUG_NEW](/previous-versions/tz7sxz99(v=vs.140)) no lugar do operador **new** para ajudar a localizar possíveis vazamentos de memória. Na versão de depuração do programa, o `DEBUG_NEW` controla o nome de arquivo e o número de linha para cada objeto que aloca. Quando você compila uma versão de lançamento do programa, o `DEBUG_NEW` resolve-se como uma operação **new** simples sem as informações de nome do arquivo e número de linha. Dessa forma, você não paga penalidade de velocidade da versão de lançamento do programa.

Se você não quiser reescrever o programa inteiro para usar `DEBUG_NEW` em vez de **new**, poderá definir esta macro em seus arquivos de origem:

```cpp
#define new DEBUG_NEW
```

Quando você faz [despejo de objeto](#BKMK_Taking_object_dumps), cada objeto alocado com `DEBUG_NEW` mostrará o arquivo e o número da linha em que foi alocado, permitindo que você localize as fontes de possíveis vazamentos de memória.

A versão de depuração da estrutura MFC usa `DEBUG_NEW` automaticamente, mas seu código não. Se você quiser os benefícios de `DEBUG_NEW`, deverá usar o `DEBUG_NEW` explicitamente ou **#define new** como mostrado acima.

[Neste tópico](#BKMK_In_this_topic)

### <a name="enabling-memory-diagnostics"></a><a name="BKMK_Enabling_memory_diagnostics"></a> Habilitando diagnóstico de memória
Para que você possa usar os recursos de diagnóstico de memória, deverá habilitar o rastreamento de diagnóstico.

**Para habilitar ou desabilitar o diagnóstico de memória**

- Chame a função global [AfxEnableMemoryTracking](/previous-versions/hzsxb6e8(v=vs.140)) para habilitar ou desabilitar o alocador de diagnóstico de memória. Como o diagnóstico de memória é ativado por padrão na biblioteca de depuração, você normalmente usará essa função para desativá-la temporariamente, o que aumenta a velocidade de execução do programa e reduz a saída de diagnóstico.

  **Para selecionar recursos de diagnóstico de memória específicos com afxMemDF**

- Se você quiser um controle mais preciso sobre os recursos de diagnóstico de memória, poderá habilitar e desabilitar seletivamente os recursos individuais de diagnóstico de memória definindo o valor da variável global [afxMemDF](/previous-versions/ahe4a83t(v=vs.140)) do MFC. Essa variável pode ter os seguintes valores conforme especificado pelo tipo enumerado **afxMemDF**.

  |Valor|Descrição|
  |-----------|-----------------|
  |**allocMemDF**|Ativar o alocador de diagnóstico de memória (padrão).|
  |**delayFreeMemDF**|Atrase a liberação de memória ao chamar `delete` ou até `free` até o programa fechar. Isso fará o programa alocar a quantidade máxima de memória possível.|
  |**checkAlwaysMemDF**|Chame [AfxCheckMemory](/cpp/mfc/reference/diagnostic-services#afxcheckmemory) toda vez que a memória for alocada ou liberada.|

  Esses valores podem ser usados em combinação executando uma operação OR lógica, como mostrado a seguir:

  ```C++
  afxMemDF = allocMemDF | delayFreeMemDF | checkAlwaysMemDF;
  ```

  [Neste tópico](#BKMK_In_this_topic)

### <a name="taking-memory-snapshots"></a><a name="BKMK_Taking_memory_snapshots"></a> Tirando instantâneos de memória

1. Crie um objeto [CMemoryState](/previous-versions/visualstudio/visual-studio-2010/2ads32e2(v=vs.100)) e chame a função de membro [CMemoryState:: Checkpoint](/cpp/mfc/reference/cmemorystate-structure#checkpoint) . Isso cria o primeiro instantâneo de memória.

2. Depois que seu programa executar as operações de alocação e desalocação de memória, crie outro objeto `CMemoryState` e chame `Checkpoint` para esse objeto. Isso obtém um segundo instantâneo do uso da memória.

3. Crie um terceiro `CMemoryState` objeto e chame sua função de membro [CMemoryState::D ifference](/cpp/mfc/reference/cmemorystate-structure#difference) , fornecendo como argumentos os dois `CMemoryState` objetos anteriores. Se houver uma diferença entre os dois estados da memória, a função `Difference` retornará um valor diferente de zero. Isso indica que alguns blocos de memória não foram desalocados.

    Esse exemplo mostra a aparência deste código:

    ```cpp
    // Declare the variables needed
    #ifdef _DEBUG
        CMemoryState oldMemState, newMemState, diffMemState;
        oldMemState.Checkpoint();
    #endif

        // Do your memory allocations and deallocations.
        CString s("This is a frame variable");
        // The next object is a heap object.
        CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );

    #ifdef _DEBUG
        newMemState.Checkpoint();
        if( diffMemState.Difference( oldMemState, newMemState ) )
        {
            TRACE( "Memory leaked!\n" );
        }
    #endif
    ```

    Observe que as instruções de verificação de memória estão entre os blocos **#ifdef _DEBUG/#endif** para que sejam compiladas somente em versões de depuração do seu programa.

    Agora que você sabe que existe um vazamento de memória, você pode usar outra função de membro, [CMemoryState::D umpstatistics](/cpp/mfc/reference/cmemorystate-structure#dumpstatistics) que o ajudará a localizá-lo.

    [Neste tópico](#BKMK_In_this_topic)

### <a name="viewing-memory-statistics"></a><a name="BKMK_Viewing_memory_statistics"></a> Exibindo estatísticas de memória
A função [CMemoryState::D ifference](/cpp/mfc/reference/cmemorystate-structure#difference) examina dois objetos de estado de memória e detecta quaisquer objetos não desalocados do heap entre os Estados inicial e final. Depois de ter obtido instantâneos de memória e comparando-os usando `CMemoryState::Difference` o, você pode chamar [CMemoryState::D umpstatistics](/cpp/mfc/reference/cmemorystate-structure#dumpstatistics) para obter informações sobre os objetos que não foram desalocados.

Considere o seguinte exemplo:

```cpp
if( diffMemState.Difference( oldMemState, newMemState ) )
{
    TRACE( "Memory leaked!\n" );
    diffMemState.DumpStatistics();
}
```

Um despejo de exemplo tem a seguinte aparência:

```cpp
0 bytes in 0 Free Blocks
22 bytes in 1 Object Blocks
45 bytes in 4 Non-Object Blocks
Largest number used: 67 bytes
Total allocations: 67 bytes
```

Os blocos livres são os blocos cuja desalocação será atrasada se `afxMemDF` tiver sido definido como `delayFreeMemDF`.

Os blocos de objeto comuns, mostrados na segunda linha, permanecem alocados no heap.

Os blocos diferentes de objeto incluem as matrizes e as estruturas alocadas com `new`. Nesse caso, quatro blocos diferentes de objeto foram alocados no heap, mas não desalocados.

`Largest number used` fornece o máximo de memória usada pelo programa a qualquer momento.

`Total allocations` fornece a quantidade total de memória usada pelo programa.

[Neste tópico](#BKMK_In_this_topic)

### <a name="taking-object-dumps"></a><a name="BKMK_Taking_object_dumps"></a> Fazendo despejos de objeto
Em um programa MFC, você pode usar [CMemoryState::D umpallobjectssince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince) para despejar uma descrição de todos os objetos no heap que não foram desalocados. `DumpAllObjectsSince` Despeja todos os objetos alocados desde o último [CMemoryState:: Checkpoint](/cpp/mfc/reference/cmemorystate-structure#checkpoint). Se nenhuma chamada de `Checkpoint` tiver ocorrido, o `DumpAllObjectsSince` despejará todos os objetos e não objetos atualmente na memória.

> [!NOTE]
> Antes de usar o despejo de objeto do MFC, você deverá [habilitar o rastreamento de diagnóstico](#BKMK_Enabling_memory_diagnostics).

> [!NOTE]
> O MFC despeja automaticamente todos os objetos vazados quando o programa sair, portanto você não precisará criar o código para despejar objetos nesse momento.

O código a seguir testa um vazamento de memória comparando dois estados de memória e despeja todos os objetos se um vazamento for detectado.

```cpp
if( diffMemState.Difference( oldMemState, newMemState ) )
{
    TRACE( "Memory leaked!\n" );
    diffMemState.DumpAllObjectsSince();
}
```

O conteúdo do despejo é semelhante ao seguinte:

```cmd
Dumping objects ->

{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long
{2} a CPerson at $51A4

Last Name: Smith
First Name: Alan
Phone #: 581-0215

{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long
```

Os números entre chaves no início da maioria das linhas especificam a ordem na qual os objetos foram alocados. O objeto alocado mais recentemente tem o número mais alto e aparece no alto do despejo.

Para obter a quantidade máxima de informações fora de um despejo de objeto, você poderá substituir a função de membro `Dump` de qualquer objeto derivado de `CObject` para personalizar o despejo do objeto.

Você pode definir um ponto de interrupção em uma alocação de memória específica configurando a variável global `_afxBreakAlloc` com o número mostrado entre chaves. Se você executar novamente o programa, o depurador interromperá a execução quando essa alocação ocorrer. Você pode em seguida analisar a pilha de chamadas para ver como o programa chegou a esse ponto.

A biblioteca de tempo de execução do C tem uma função semelhante, [_CrtSetBreakAlloc](/cpp/c-runtime-library/reference/crtsetbreakalloc), que você pode usar para alocações de tempo de execução c.

[Neste tópico](#BKMK_In_this_topic)

#### <a name="interpreting-memory-dumps"></a><a name="BKMK_Interpreting_memory_dumps"></a> Interpretando despejos de memória
Observe este despejo de objeto com mais detalhes:

```cmd
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long
{2} a CPerson at $51A4

Last Name: Smith
First Name: Alan
Phone #: 581-0215

{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long
```

O programa que gerou este despejo tinha apenas duas alocações explícitas- uma na pilha e uma no heap:

```cpp
// Do your memory allocations and deallocations.
CString s("This is a frame variable");
// The next object is a heap object.
CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
```

O construtor `CPerson` usa três argumentos que são os ponteiros para `char`, que são usados para inicializar variáveis de membro `CString`. No despejo de memória, você pode ver o objeto `CPerson` junto com três blocos diferentes de objeto (3, 4 e 5). Eles mantêm os caracteres para as variáveis de membro `CString` e não serão excluídos quando o destruidor do objeto `CPerson` for invocado.

O bloco número 2 é o próprio objeto `CPerson`. `$51A4` representa o endereço do bloco e é seguido pelos conteúdos do objeto, que eram gerados pelo `CPerson`::`Dump` quando chamados pelo [DumpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince).

Você pode determinar a qual bloco o número 1 está associado com a variável de quadro `CString` devido ao número e ao tamanho da sequência, que corresponde ao número de caracteres na variável `CString` do quadro. As variáveis alocadas no quadro são desalocadas automaticamente quando o quadro sai do escopo.

**Variáveis de quadro**

Em geral, você não precisa se preocupar com objetos heap associados a variáveis do quadro porque eles são desalocados automaticamente quando as variáveis do quadro saem do escopo. Para evitar a confusão nos despejos de diagnóstico de memória, você deve posicionar suas chamadas para `Checkpoint` de modo que fiquem fora do escopo de variáveis do quadro. Por exemplo, coloque colchetes de escopo em volta do código de alocação anterior, como mostrado a seguir:

```cpp
oldMemState.Checkpoint();
{
    // Do your memory allocations and deallocations ...
    CString s("This is a frame variable");
    // The next object is a heap object.
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
}
newMemState.Checkpoint();
```

Com os colchetes de escopo no lugar, o despejo de memória para este exemplo ocorre da seguinte maneira:

```cmd
Dumping objects ->

{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long
{2} a CPerson at $51A4

Last Name: Smith
First Name: Alan
Phone #: 581-0215
```

**Alocações diferentes de objeto**

Observe que algumas alocações são objetos (como `CPerson`) e algumas são alocações diferentes de objeto. As "alocações diferentes de objeto" são alocações para os objetos não derivados de `CObject` ou alocações de tipos C primitivos como `char`, `int` ou `long`. Se a classe derivada de <strong>CObject</strong> aloca o espaço adicional, por exemplo, para buffers internos, esses objetos mostrarão as alocações de objeto e diferentes de objeto.

**Evitando vazamentos de memória**

Observe no código acima que o bloco de memória associado à variável do quadro `CString` foi desalocado automaticamente e não aparece como um vazamento de memória. A desalocação automática associada a regras de escopo é responsável pela maioria dos vazamentos de memória associados a variáveis do quadro.

Para os objetos alocados no heap, no entanto, você deve excluir explicitamente o objeto para evitar um vazamento de memória. Para limpar o último vazamento de memória no exemplo anterior, exclua o objeto `CPerson` alocado no heap, da seguinte maneira:

```cpp
{
    // Do your memory allocations and deallocations.
    CString s("This is a frame variable");
    // The next object is a heap object.
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
    delete p;
}
```

[Neste tópico](#BKMK_In_this_topic)

#### <a name="customizing-object-dumps"></a><a name="BKMK_Customizing_object_dumps"></a> Personalizando despejos de objeto
Quando você deriva uma classe de [CObject](/cpp/mfc/reference/cobject-class), pode substituir a função de membro `Dump` para fornecer informações adicionais quando usa [DumpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince) para despejar objetos para a [janela de Saída](../ide/reference/output-window.md).

A função `Dump` grava uma representação textual das variáveis de membro do objeto em um contexto de despejo ([CDumpContext](/cpp/mfc/reference/cdumpcontext-class)). O contexto de despejo é semelhante a um fluxo de E/S. Você pode usar o operador Append ( **<<** ) para enviar dados para um `CDumpContext` .

Quando você substitui a função `Dump`, primeiro deve chamar a versão da classe base do `Dump` para despejar o conteúdo do objeto da classe base. Em seguida, gere uma descrição e um valor textuais para cada variável de membro da sua classe derivada.

A declaração da função `Dump` é semelhante a esta:

```cpp
class CPerson : public CObject
{
public:
#ifdef _DEBUG
    virtual void Dump( CDumpContext& dc ) const;
#endif

    CString m_firstName;
    CString m_lastName;
    // And so on...
};
```

Como o objeto de despejo só faz sentido quando você estiver depurando seu programa, a declaração da função `Dump` é envolvida com um bloco **#ifdef _DEBUG / #endif**.

No exemplo a seguir, a função `Dump` primeiro chama a função `Dump` para a sua classe base. Em seguida, ela grava uma breve descrição de cada variável de membro junto com o valor do membro no fluxo de diagnóstico.

```cpp
#ifdef _DEBUG
void CPerson::Dump( CDumpContext& dc ) const
{
    // Call the base class function first.
    CObject::Dump( dc );

    // Now do the stuff for our specific class.
    dc << "last name: " << m_lastName << "\n"
        << "first name: " << m_firstName << "\n";
}
#endif
```

Você deve fornecer um argumento de `CDumpContext` para especificar para onde a saída de despejo irá. A versão de depuração do MFC fornece um objeto `CDumpContext` predefinido chamado `afxDump` que envia a saída para o depurador.

```cpp
CPerson* pMyPerson = new CPerson;
// Set some fields of the CPerson object.
//...
// Now dump the contents.
#ifdef _DEBUG
pMyPerson->Dump( afxDump );
#endif
```

[Neste tópico](#BKMK_In_this_topic)

## <a name="reducing-the-size-of-an-mfc-debug-build"></a><a name="BKMK_Reducing_the_size_of_an_MFC_Debug_build"></a> Reduzindo o tamanho de um build de depuração do MFC
As informações de depuração para um aplicativo MFC grande pode utilizar muito espaço em disco. Você pode usar um destes procedimentos para reduzir o tamanho:

1. Reconstrua as bibliotecas do MFC usando a opção [/Z7,/Zi,/Zi (formato de informações de depuração)](/cpp/build/reference/z7-zi-zi-debug-information-format) , em vez de **/Z7**. Essas opções criam um único arquivo de banco de dados do programa (PDB) que contém informações de depuração para a biblioteca inteira, reduzindo a redundância e economizando espaço.

2. Reconstrua as bibliotecas do MFC sem informações de depuração (nenhuma opção [/Z7,/Zi,/Zi (formato de informações de depuração)](/cpp/build/reference/z7-zi-zi-debug-information-format) ). Nesse caso, a falta de informações de depuração impedirão que você use a maioria dos recursos do depurador no código da biblioteca MFC, mas como as bibliotecas MFC já estão completamente depuradas, isso pode não ser um problema.

3. Crie seu próprio aplicativo com informações de depuração para os módulos selecionados apenas como descrito abaixo.

    [Neste tópico](#BKMK_In_this_topic)

### <a name="building-an-mfc-app-with-debug-information-for-selected-modules"></a><a name="BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules"></a> Criando um aplicativo do MFC com informações de depuração para os módulos selecionados
Criar os módulos selecionados com as bibliotecas de depuração MFC permite usar a depuração e outros recursos nesses módulos. Esse procedimento usa as configurações de depuração e de versão do projeto, exigindo assim as alterações descritas nas etapas a seguir (e também fazendo uma "Recompilar tudo" necessária quando uma compilação de versão completa é necessária).

1. No Gerenciador de Soluções, selecione o projeto.

2. No menu **Exibir**, selecione **Páginas de Propriedades**.

3. Primeiro, você criará uma nova configuração de projeto.

   1. Na caixa de diálogo ** \<Project> páginas de propriedades** , clique no botão **Configuration Manager** .

   2. Na [caixa de diálogo do Configuration Manager](/previous-versions/visualstudio/visual-studio-2010/t1hy4dhz(v=vs.100)), localize seu projeto na grade. Na coluna **configuração** , selecione **\<New...>** .

   3. Na [caixa de diálogo Nova Configuração de Projeto](/previous-versions/visualstudio/visual-studio-2010/0eh8w4cf(v=vs.100)), digite um nome para a nova configuração, por exemplo “Depuração parcial”, na caixa **Nome de Configuração do Projeto**.

   4. Na lista **Copiar Configurações de**, escolha **Versão**.

   5. Clique em **OK** para fechar a caixa de diálogo **nova configuração de projeto** .

   6. Feche a caixa de diálogo **Configuration Manager**.

4. Agora, você definirá opções para o projeto inteiro.

   1. Na caixa de diálogo **Páginas de Propriedades**, na pasta **Propriedades de Configuração**, selecione a categoria **Geral**.

   2. Na grade de configurações de projeto, expanda **Padrões de Projeto** (se necessário).

   3. Em **Padrões de Projeto**, localize **Uso do MFC**. A configuração atual é exibida na coluna direita da grade. Clique na configuração atual e altere-a para **Usar MFC em uma Biblioteca Estática**.

   4. No painel esquerdo da caixa de diálogo **Páginas de Propriedades**, abra a pasta **C/C++** e selecione **Pré-Processador**. Na grade de propriedades, localize **Definições do Pré-processador** e substitua "NDEBUG" por "_DEBUG".

   5. No painel esquerdo da caixa de diálogo **Páginas de Propriedades**, abra a pasta **Vinculador** e selecione a categoria **Entrada**. Na grade de propriedades, localize **Dependências Adicionais**. Na definição de **Dependências Adicionais**, digite "NAFXCWD.LIB" e "LIBCMT".

   6. Clique em **OK** para salvar as novas opções de criação e feche a caixa de diálogo **Páginas de Propriedades**.

5. No menu **Compilar**, selecione **Recompilar**. Isso remove todas as informações de depuração de seus módulos, mas não afeta a biblioteca MFC.

6. Agora você deve adicionar as informações de depuração de volta para os módulos selecionados em seu aplicativo. Lembre-se de que você pode definir pontos de interrupção e executar outras funções de depurador apenas nos módulos que você compilou com informações de depuração. Para cada arquivo de projeto em que você quer incluir informações de depuração, execute as seguintes etapas:

   1. No Gerenciador de Soluções, abra a pasta **Arquivos de Origem** localizada em seu projeto.

   2. Selecione o arquivo para o qual você quer definir informações de depuração.

   3. No menu **Exibir**, selecione **Páginas de Propriedades**.

   4. Na caixa de diálogo **Páginas de Propriedades**, na pasta **Definições de Configuração**, abra a pasta **C/C++** e, em seguida, selecione a categoria **Geral**.

   5. Na grade de propriedades, localize **Formato de Informação de Depuração**.

   6. Clique nas configurações de **Formato de Informação de Depuração** e selecione a opção desejada (normalmente **/ZI**) para obter as informações de depuração.

   7. Se você estiver usando um aplicativo gerado por assistente ou se tiver cabeçalhos pré-compilado, será preciso desativar os cabeçalhos pré-compilados ou recompilá-los antes de compilar os outros módulos. Caso contrário, você receberá o aviso C4650 e mensagens de erro C2855. Você pode desativar cabeçalhos pré-compilados alterando a configuração **Criar/usar cabeçalhos pré-compilados** na caixa de diálogo ** \<Project> Propriedades** (pasta**Propriedades de configuração** , subpasta **C/C++** , categoria **cabeçalhos pré-compilados** ).

7. No menu **Compilar**, selecione **Compilar** para recompilar os arquivos de projeto que estão desatualizados.

   Como alternativa à técnica descrita neste tópico, você pode usar um makefile externo para definir opções individuais para cada arquivo. Nesse caso, para vincular com as bibliotecas de depuração MFC, você deverá definir o sinalizador [_DEBUG](/cpp/c-runtime-library/debug) para cada módulo. Se você quiser usar bibliotecas de versão MFC, deverá definir NDEBUG. Para obter mais informações sobre como escrever makefiles externos, confira [Referência de NMAKE](/cpp/build/running-nmake).

   [Neste tópico](#BKMK_In_this_topic)

## <a name="see-also"></a>Confira também
[Depurando código nativo](../debugger/debugging-native-code.md)
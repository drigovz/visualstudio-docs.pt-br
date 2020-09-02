---
title: Encontrando vazamentos de memória usando a biblioteca CRT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- breakpoints, on memory allocation
- _CrtMemState
- _CrtMemCheckpoint
- memory leaks
- _CrtMemDifference
- memory leaks, detecting and isolating
- _CrtDumpMemoryLeaks
- _CrtSetBreakAlloc
- _crtBreakAlloc
- _CrtSetReportMode
- memory, debugging
- _CrtMemDumpStatistics
- debugging memory leaks
- _CRTDBG_MAP_ALLOC
- _CrtSetDbgFlag
ms.assetid: cf6dc7a6-cd12-4283-b1b6-ea53915f7ed1
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 831cae8d83bc26e05b80d6948a3168a6e6a387c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682432"
---
# <a name="finding-memory-leaks-using-the-crt-library"></a>Localizando perdas de memória usando a biblioteca CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vazamentos de memória, definidos como a falha em desalocar corretamente a memória anteriormente alocada, estão entre os bugs mais sutis e difíceis de detectar em aplicativos C/C++. Um vazamento de memória pequeno não pode ser observado no início, mas ao longo do tempo, um vazamento de memória progressivo pode causar os sintomas que variam de desempenho reduzido a falhar quando o aplicativo é executado sem memória. Pior, um aplicativo de escape que usa toda a memória disponível pode causar a falha de outro aplicativo, criando a confusão a respeito de que o aplicativo é responsável. Até mesmo vazamentos de memória aparentemente inofensivos podem ser sintomáticos de outros problemas que devem ser corrigidos.  
  
 O depurador do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e as bibliotecas em tempo de execução (CRT) do C fornecem os meios para detectar e identificar vazamentos de memória.  
  
## <a name="enabling-memory-leak-detection"></a>Habilitando a detecção de vazamento de memória  
 As ferramentas principais para detectar vazamentos de memória são o depurador e as funções da heap de depuração das bibliotecas em tempo de execução (CRT) do C.  
  
 Para ativar as funções da heap de depuração, inclua as seguintes instruções em seu programa:  
  
```  
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  
  
 Para que as funções CRT funcionem corretamente, as instruções `#include` devem seguir a ordem mostrada aqui.  
  
 Incluir CRTDBG. h mapeia as `malloc` funções e [gratuitas](https://msdn.microsoft.com/library/74ded9cf-1863-432e-9306-327a42080bb8) para suas versões de depuração, [_malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb) e `free` , que controlam a alocação e a desalocação da memória. Esse mapeamento ocorre apenas em compilações de depuração, que tem `_DEBUG`. Compilações lançadas usam as funções `malloc` e `free`.  
  
 A declaração de `#define` mapeia uma versão de base de funções heap de CRT para a versão de depuração correspondente. Se você omitir a instrução `#define`, o despejo de vazamento de memória será menos detalhado.  
  
 Após ser habilitado, o heap de depuração funciona usando essas declarações. Você poderá fazer uma chamada a `_CrtDumpMemoryLeaks` antes de um ponto de saída do aplicativo para exibir um relatório de vazamento de memória quando seu aplicativo for encerrado:  
  
```  
_CrtDumpMemoryLeaks();  
```  
  
 Se o aplicativo tiver várias saídas, você não precisará fazer uma chamada manualmente para [_CrtDumpMemoryLeaks](https://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c) em todos os pontos de saída. Uma chamada para `_CrtSetDbgFlag` no início do seu aplicativo causará uma chamada automática para `_CrtDumpMemoryLeaks` em cada ponto de saída. Você deve definir os dois campos de bits mostrados aqui:  
  
```  
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  
  
 Por padrão, a saída `_CrtDumpMemoryLeaks` emite o relatório de vazamento de memória para o painel **Depurar** da janela de **Saída**. Você pode usar `_CrtSetReportMode` para redirecionar o relatório para outro local.  
  
 Se você usar uma biblioteca, a biblioteca poderá redefinir a saída para outro local. Nesse caso, você pode definir o local de saída de volta para a janela de **saída** , como mostrado aqui:  
  
```  
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  
  
## <a name="interpreting-the-memory-leak-report"></a>Interpretando o relatório de vazamento de memória  
 Se seu aplicativo não definir `_CRTDBG_MAP_ALLOC` , [_CrtDumpMemoryLeaks](https://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c) exibirá um relatório de vazamento de memória parecido com este:  
  
```  
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 Se o seu aplicativo definir `_CRTDBG_MAP_ALLOC`, o relatório de vazamento de memória se parecerá com este:  
  
```  
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
 normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 A diferença é que o segundo relatório mostra o nome do arquivo e número da linha no qual a memória vazada é atribuída primeiro.  
  
 Se você definir `_CRTDBG_MAP_ALLOC` ou não, o relatório de vazamento de memória exibirá as seguintes informações:  
  
- O número de alocação de memória, que é `18` nesse exemplo  
  
- O [tipo de bloco](https://msdn.microsoft.com/e2f42faf-0687-49e7-aa1f-916038354f97), que está `normal` neste exemplo.  
  
- O número de alocação de memória hexadecimal, que é `0x00780E80` nesse exemplo.  
  
- O tamanho do bloco, `64 bytes` neste exemplo.  
  
- Os primeiros 16 bytes de dados no bloco, no formulário hexadecimal.  
  
  O relatório de vazamento de memória identifica um bloco de memória como normal, cliente, ou CRT. Um *bloco normal* é a memória comum atribuída pelo seu programa. Um *bloco de cliente* é um tipo especial de bloco de memória usado por programas MFC para os objetos que exigem um destruidor. O operador MFC `new` cria um bloco normal ou um bloco de cliente, como apropriado para o objeto que estiver sendo criado. Um *bloco de CRT* é atribuído pela biblioteca de CRT para seu próprio uso. A biblioteca de CRT trata a desalocação desses blocos. Portanto, é improvável que você os veja no relatório de vazamento de memória a menos que algo esteja significativamente errado, por exemplo, a biblioteca de CRT está danificada.  
  
  Há dois tipos de outros blocos de memória que nunca aparecem nos relatórios de escape de memória. Um *bloco gratuito* é a memória que foi liberada. Isso significa que não está vazado, por definição. Um *bloco de ignorar* é a memória que você marcou explicitamente para excluí-lo do relatório de vazamento de memória.  
  
  Essas técnicas funcionam para a memória alocada usando a função de CRT `malloc` padrão. No entanto, se o seu programa alocar memória usando o operador C++, `new` você só poderá ver o número de arquivo e de linha em que a implementação de `operator new` chamadas globais `_malloc_dbg` no relatório de vazamento de memória. Como esse comportamento não é muito útil, você pode alterá-lo para relatar a linha que fez a alocação usando uma macro parecida com esta: 
 
```cpp  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  
  
Agora você pode substituir o `new` operador usando a `DBG_NEW` macro em seu código. Em compilações de depuração, isso usa uma sobrecarga de global `operator new` que usa parâmetros adicionais para o tipo de bloco, o arquivo e o número de linha. Essa sobrecarga de `new` chamadas `_malloc_dbg` para registrar as informações extras. Quando você usa o `DBG_NEW` , os relatórios de vazamento de memória mostram o nome de arquivo e o número de linha onde os objetos vazados foram alocados. Em compilações de varejo, ele usa o padrão `new` . (Não recomendamos que você crie uma macro de pré-processador chamada `new` ou qualquer outra palavra-chave de linguagem.) Aqui está um exemplo da técnica:  
  
```cpp  
// debug_new.cpp
// compile by using: cl /EHsc /W4 /D_DEBUG /MDd debug_new.cpp
#define _CRTDBG_MAP_ALLOC
#include <cstdlib>
#include <crtdbg.h>

#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif

struct Pod {
    int x;
};

void main() {
    Pod* pPod = DBG_NEW Pod;
    pPod = DBG_NEW Pod; // Oops, leaked the original pPod!
    delete pPod;

    _CrtDumpMemoryLeaks();
}
```  
  
Quando você executa esse código no depurador no Visual Studio, a chamada para `_CrtDumpMemoryLeaks` gera um relatório na janela de **saída** que é semelhante a esta:  
  
```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  
  
Isso informa que a alocação vazada estava na linha 20 de debug_new. cpp.  
  
## <a name="setting-breakpoints-on-a-memory-allocation-number"></a>Pontos de interrupção em um Número de Alocação de Memória  
 O número de alocação de memória informa quando um bloco de memória vazado tiver sido atribuído. Um bloco com uma alocação de memória de 18, por exemplo, é o 18º bloco de memória alocado durante a execução do aplicativo. O relatório de CRT conta todas as alocações bloco de memória durante a execução. Isso inclui as alocações pela biblioteca de CRT e por outras bibliotecas, como o MFC. Portanto, um bloco com um número de alocação de memória de 18 não pode ser o 18º bloco de memória atribuído pelo seu código. Normalmente, não será.  
  
 Você pode usar o número de alocação para definir um ponto de interrupção na alocação da memória.  
  
#### <a name="to-set-a-memory-allocation-breakpoint-using-the-watch-window"></a>Para definir um ponto de interrupção de alocação de memória usando a janela Inspeção  
  
1. Defina um ponto de interrupção no início do seu aplicativo, e depois inicie seu aplicativo.  
  
2. Quando o aplicativo é interrompido no ponto de interrupção, a janela **Watch** .  
  
3. Na janela **inspecionar** , digite `_crtBreakAlloc` a coluna **nome** .  
  
    Se estiver usando a versão com multithread da DLL da biblioteca CRT (a opção /MD), inclua o operador de contexto: `{,,ucrtbased.dll}_crtBreakAlloc`  
  
4. Pressione **retornar**.  
  
    O depurador avalia a chamada e coloca o resultado na coluna de **Valor**. Esse valor será -1 se você não definir nenhum ponto de interrupção nas alocações de memória.  
  
5. Na coluna **valor** , substitua o valor mostrado pelo número de alocação da alocação de memória onde você deseja interromper.  
  
   Após definir um ponto de interrupção em um número de alocação de memória, você poderá continuar a depuração. Tenha cuidado ao executar o programa nas mesmas condições que a execução anterior de modo que a ordem de alocação de memória não seja alterada. Quando o programa for interrompido na alocação de memória especificada, você poderá usar a janela **pilha de chamadas** e outras janelas do depurador para determinar as condições sob as quais a memória foi alocada. Em seguida, você pode continuar a execução para observar o que acontece ao objeto e determinar o motivo dele não ser deslocado corretamente.  
  
   Definindo um ponto de interrupção de dados no objeto também pode ser útil. Para obter mais informações, consulte [usando pontos de interrupção](../debugger/using-breakpoints.md).  
  
   Você também pode definir pontos de interrupção de alocação de memória no código. Há duas maneiras de fazer isso:  
  
```  
_crtBreakAlloc = 18;  
```  
  
 ou:  
  
```  
_CrtSetBreakAlloc(18);  
```  
  
## <a name="comparing-memory-states"></a>Comparando estados de memória  
 Outra técnica para localizar vazamentos de memória envolve pegar instantâneos do estado da memória do aplicativo em pontos-chave. Para tirar um instantâneo do estado da memória em um determinado ponto em seu aplicativo, crie uma estrutura de **_CrtMemState** e passe-a para a `_CrtMemCheckpoint` função. Esta função preenche a estrutura com uma forma instantânea do estado de memória atual:  
  
```  
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
  
```  
  
 `_CrtMemCheckpoint` preenche a estrutura com um instantâneo do estado da memória atual.  
  
 Para gerar o conteúdo de uma estrutura de **_CrtMemState** , passe a estrutura para a `_ CrtMemDumpStatistics` função:  
  
```  
_CrtMemDumpStatistics( &s1 );  
  
```  
  
 `_ CrtMemDumpStatistics` gera um despejo de estado de memória semelhante a este:  
  
```  
0 bytes in 0 Free Blocks.  
0 bytes in 0 Normal Blocks.  
3071 bytes in 16 CRT Blocks.  
0 bytes in 0 Ignore Blocks.  
0 bytes in 0 Client Blocks.  
Largest number used: 3071 bytes.  
Total allocations: 3764 bytes.  
  
```  
  
 Para determinar se um vazamento de memória ocorreu em uma seção de código, você pode capturar instantâneos do estado da memória antes e após a seção e, em seguida, usar `_ CrtMemDifference` para comparar os dois estados:  
  
```  
_CrtMemCheckpoint( &s1 );  
// memory allocations take place here  
_CrtMemCheckpoint( &s2 );  
  
if ( _CrtMemDifference( &s3, &s1, &s2) )  
   _CrtMemDumpStatistics( &s3 );  
```  
  
 `_CrtMemDifference` compara os Estados de memória `s1` e `s2` retorna um resultado em ( `s3` ) que é a diferença de `s1` e `s2` .  
  
 Uma técnica para localizar vazamentos de memória começa colocando chamadas de `_CrtMemCheckpoint` no início e fim do seu aplicativo, depois usando `_CrtMemDifference` para comparar os resultados. Se `_CrtMemDifference` mostra um vazamento de memória, você pode adicionar mais chamadas de `_CrtMemCheckpoint` para dividir seu programa usando uma busca binária até ter isolado a fonte do vazamento.  
  
## <a name="false-positives"></a>Falsos positivos  
 Em alguns casos, `_CrtDumpMemoryLeaks` poderá dar falsas indicações de vazamentos de memória. Isso pode ocorrer se você usar uma biblioteca que marca alocações internas como _NORMAL_BLOCKs em vez de `_CRT_BLOCK`s ou de `_CLIENT_BLOCK`s. Nesse caso, `_CrtDumpMemoryLeaks` não é capaz de reconhecer a diferença entre alocações de usuário e alocações internas de biblioteca. Se os destruidores globais das alocações de biblioteca forem executados após o ponto onde você chama `_CrtDumpMemoryLeaks`, cada alocação interna da biblioteca será relatada como um vazamento de memória. As versões anteriores de biblioteca padrão do modelo, anteriores do Visual Studio .NET, causaram `_CrtDumpMemoryLeaks` para relatar falsos positivos, mas este foram corrigidos em versões recentes.  
  
## <a name="see-also"></a>Consulte Também  
 [Detalhes de heap de depuração CRT](../debugger/crt-debug-heap-details.md)   
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)

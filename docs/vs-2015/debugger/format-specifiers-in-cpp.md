---
title: Especificadores de formato em C++ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- QuickWatch dialog box, format specifiers in C++
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- expressions [C++], format specifiers
- specifiers, watch variable format
- specifiers
- Watch window, format specifiers in C++
- watch variable symbols
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 0f6f3b7c-ce2c-4b4d-b14f-7589dbed5444
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9f620cbf5d522b99965268f35c00ff8e874f1542
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838727"
---
# <a name="format-specifiers-in-c"></a>Especificadores de formato em C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode alterar o formato no qual um valor é exibido na janela de **inspeção** usando especificadores de formato.  
  
 Você também pode usar especificadores de formato na janela **imediata** , a janela de **comando** e até mesmo em janelas de origem. Se você pausar em uma expressão nessas janelas, o resultado aparecerá em uma DataTip. A exibição DataTip reflete o especificador de formato.  
  
> [!NOTE]
> O depurador nativo do Visual Studio foi alterado para um novo mecanismo de depuração. Como parte dessa alteração, alguns especificadores de formato novos foram adicionados e alguns antigos foram removidos. O depurador mais antigo ainda é usado quando você faz a depuração de Interop (nativo e de gerenciamento misto) com C++/CLI. As seções a seguir neste tópico mostram os especificadores de formato para cada mecanismo de depuração.  
> 
> - Os [especificadores de formato](#BKMK_Visual_Studio_2012_format_specifiers) descrevem os especificadores de formato no novo mecanismo de depuração.  
>   - Os [especificadores de formato para a depuração de interoperabilidade com C++/CLI](#BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue) descreve os especificadores de formato no mecanismo de depuração mais antigo.  
  
## <a name="using-format-specifiers"></a>Usando especificadores de formato  
 Se você tiver o seguinte código:  
  
```cpp  
int main() {  
    int my_var1 = 0x0065;  
    int my_var2 = 0x0066;  
    int my_var3 = 0x0067;  
}  
```  
  
 Adicione a `my_var1` variável à janela de **inspeção** (durante a depuração, **depuração/Windows/inspeção/inspeção 1**) e defina a exibição como hexadecimal (na janela **Watch** , clique com o botão direito do mouse na variável e selecione **exibição hexadecimal**). Agora, o janela Inspeção mostra que ele contém o valor 0x0065. Para ver esse valor expresso como um caractere em vez de um inteiro, na coluna nome, após o nome da variável, adicione o especificador de formato de caractere **, c**. A coluna **valor** agora aparece com **101 ' e '**.  
  
 ![WatchFormatCPlus1](../debugger/media/watchformatcplus1.png "WatchFormatCPlus1")  
  
## <a name="format-specifiers"></a><a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Especificadores de formato  
 As tabelas a seguir mostram os especificadores de formato que você pode usar no Visual Studio. Não há suporte para especificadores em negrito para depuração de interoperabilidade com C++/CLI.  
  
|Especificador|Formatar|Valor de inspeção original|Valor exibido|  
|---------------|------------|--------------------------|---------------------|  
|d|inteiro decimal|0x00000066|102|  
|o|inteiro octal não assinado|0x00000066|000000000146|  
|x<br /><br /> **h**|inteiro hexadecimal|102|0xcccccccc|  
|X<br /><br /> **H**|inteiro hexadecimal|102|0xCCCCCCCC|  
|c|caractere único|0x0065, c|101 'e'|  
|s|Cadeia de caracteres const char *|\<location> "Olá, mundo"|“Olá Mundo”|  
|**SB**|Cadeia de caracteres const char *|\<location> "Olá, mundo"|hello world|  
|s8|Cadeia de caracteres const char *|\<location> "Olá, mundo"|“Olá Mundo”|  
|**s8b**|Cadeia de caracteres const char *|\<location> "Olá, mundo"|“Olá Mundo”|  
|su|const wchar_t * const<br /><br /> char16_t \* cadeia de caracteres|\<location> L "Olá mundo"|L"hello world"<br /><br /> u "Olá mundo"|  
|sub|const wchar_t * const<br /><br /> char16_t \* cadeia de caracteres|\<location> L "Olá mundo"|hello world|  
|bstr|Cadeia de caracteres BSTR|\<location> L "Olá mundo"|L "Olá mundo"|  
|**s32**|Cadeia de caracteres UTF-32|\<location> U "Olá mundo"|U "Olá mundo"|  
|**s32b**|Cadeia de caracteres UTF-32 (sem aspas)|\<location> U "Olá mundo"|hello world|  
|**en**|enum|Saturday(6)|Sábado|  
|**hv**|Tipo de ponteiro – indica que o valor do ponteiro sendo inspecionado é o resultado da alocação de heap de uma matriz, por exemplo, `new int[3]` .|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, …}|  
|**na**|Inibe o endereço de memória de um ponteiro para um objeto.|\<location>, {member = Value...}|{member = valor...}|  
|**segunda**|Exibe somente as informações de classe base, ignorando classes derivadas|`(Shape*) square` inclui a classe base e as informações de classe derivada|Exibe somente informações da classe base|  
|h|Código de erro HRESULT ou Win32. (O depurador agora decodifica HRESULTs automaticamente. Portanto, esse especificador não é necessário nesses casos.|S_OK|S_OK|  
|wc|Sinalizador de classe do Windows|0x0010|WC_DEFAULTCHAR|  
|wm|Números de mensagens do Windows|16|WM_CLOSE|  
|!|formato bruto, ignorando qualquer personalização de exibições de tipo de dados|\<customized representation>|4|  
  
> [!NOTE]
> Quando o especificador de formato **HV** estiver presente, o depurador tentará determinar o comprimento do buffer e exibirá o número apropriado de elementos. Como nem sempre é possível que o depurador encontre o tamanho exato do buffer de uma matriz, você deve usar um especificador de tamanho `(pBuffer,[bufferSize])` sempre que possível. O especificador de formato **HV** é destinado a cenários em que o tamanho do buffer não está prontamente disponível  
  
### <a name="size-specifiers-for-pointers-as-arrays"></a><a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Especificadores de tamanho para ponteiros como matrizes  
 Se você tiver um ponteiro para um objeto que queira exibir como uma matriz, pode usar um inteiro ou uma expressão para especificar o número de elementos da matriz:  
  
|Especificador|Formatar|Valor da inspeção original|Valor exibido|  
|---------------|------------|---------------------------|---------------------|  
|n|Inteiro decimal ou inteiro **hexadecimal**|pBuffer,[32]<br /><br /> pBuffer,**[0x20]**|Exibe `pBuffer` como uma matriz de elementos 32.|  
|**exp**|Uma expressão C++ válida que é avaliada como um inteiro.|pBuffer,[bufferSize]|Exibe pBuffer como uma matriz de `bufferSize` elementos.|  
|**expand(n)**|Uma expressão C++ válida que é avaliada como um inteiro|pBuffer, expand(2)|Exibe o terceiro elemento de  `pBuffer`|  
  
## <a name="format-specifiers-for-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> Especificadores de formato para depuração de interoperabilidade com C++/CLI  
 Não há suporte para especificadores em **negrito** apenas para depuração de código nativo e C++/CLI.  
  
|Especificador|Formatar|Valor de inspeção original|Valor exibido|  
|---------------|------------|--------------------------|---------------------|  
|**d, i**|inteiro decimal assinado|0xF000F065|-268373915|  
|**u**|inteiro decimal não assinado|0x0065|101|  
|o|inteiro octal não assinado|0xF065|0170145|  
|x,X|Inteiro hexadecimal|61541|0x0000f065|  
|**l,h**|prefixo longo ou curto para: d, i, u, o, x, X|00406042|0x0c22|  
|**f**|ponto flutuante assinado|(3./2.), f|1.500000|  
|**Oriental**|notação científica assinada|(3.0/2.0)|1.500000e+000|  
|**g**|ponto flutuante assinado ou notação científica assinada, o que for menor|(3.0/2.0)|1.5|  
|c|caractere único|\<location>|101 'e'|  
|s|const char *|\<location>|“Olá Mundo”|  
|su|const wchar_t*<br /><br /> const char16_t\*|\<location>|L"hello world"|  
|sub|const wchar_t*<br /><br /> const char16_t\*|\<location>|hello world|  
|s8|const char *|\<location>|“Olá Mundo”|  
|h|Código de erro HRESULT ou Win32. (O depurador agora decodifica HRESULTs automaticamente. Portanto, esse especificador não é necessário nesses casos.|S_OK|S_OK|  
|wc|Sinalizador de classe do Windows.|0x00000040,|WC_DEFAULTCHAR|  
|wm|Números de mensagens do Windows|0x0010|WM_CLOSE|  
|!|formato bruto, ignorando qualquer personalização de exibições de tipo de dados|\<customized representation>|4|  
  
### <a name="format-specifiers-memory-locations-in-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> Formatar especificadores de memória locais na depuração de interoperabilidade com C++/CLI  
 A tabela a seguir contém os símbolos de formatação usados para locais de memória. Você pode usar um especificador de local da memória com qualquer valor ou expressão que seja avaliada como um local.  
  
|Símbolo|Formatar|Valor de inspeção original|Valor exibido|  
|------------|------------|--------------------------|---------------------|  
|**Massachusetts**|Caracteres ASCII na base 64|0x0012ffac|0x0012ffac .4...0...".0W&.......1W&.0.:W..1...."..1.JO&.1.2.."..1...0y....1|  
|**m**|16 bytes em hexadecimal, seguidos caracteres ASCII na base 16|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|  
|**MBS**|16 bytes em hexadecimal, seguidos caracteres ASCII na base 16|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|  
|**MW**|8 palavras|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|  
|**md**|4 palavra duplas|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|  
|**MQ**|2 palavras quádruplas|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|  
|**Mu**|Caracteres de 2 bytes (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|  
  
### <a name="size-specifier-for-pointers-as-arrays-in-interop-debugging-with-cclit"></a><a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> Especificador de tamanho para ponteiros como matrizes na depuração de interoperabilidade com C++/CLIt  
 Se você tiver um ponteiro para um objeto que você deseja exibir como uma matriz, pode usar um inteiro para especificar o número de elementos da matriz:  
  
|Especificador|Formatar|Expression|Valor exibido|  
|---------------|------------|----------------|---------------------|  
|n|Inteiro decimal|pBuffer[32]|Exibe `pBuffer` como uma matriz de elementos 32.|

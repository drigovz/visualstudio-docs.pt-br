---
title: Usando os verificadores de Diretrizes Principais do C++ | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: fffa4cec6a2bd7a340b90776ac20dc486f28045b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "84173545"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Usando os verificadores de Diretrizes Principais do C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A Diretrizes Principais do C++ é um conjunto portátil de diretrizes, regras e práticas recomendadas sobre codificação em C++ criado por especialistas e designers do C++.  O Visual Studio agora dá suporte a pacotes de suplemento que criam regras adicionais para as ferramentas de análise de código para verificar a conformidade do seu código com o Diretrizes Principais do C++ e sugerir melhorias.  
  
## <a name="the-c-core-guidelines-project"></a>O projeto Diretrizes Principais do C++  
 Criado por Bjarne Stroustrup e outros, o Diretrizes Principais do C++ é um guia para usar C++ moderno com segurança e eficiência. As diretrizes enfatizam a segurança de tipo estático e a segurança de recursos. Eles identificam maneiras de eliminar ou minimizar as partes mais propensas a erros da linguagem e sugerem como tornar seu código mais simples e mais funcional de maneira confiável. Essas diretrizes são mantidas pelo Standard C++ Foundation. Para saber mais, consulte a documentação, [diretrizes principais do C++](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)e acessar os arquivos de projeto de documentação diretrizes principais do C++ no [GitHub](https://github.com/isocpp/CppCoreGuidelines).  
  
 A Microsoft dá suporte à Diretrizes Principais do C++ esforço fazendo Verificação Principal do C++ conjuntos de regras de análise de código que você pode adicionar a seus projetos usando um pacote NuGet. O pacote é denominado Microsoft. CppCoreCheck e está disponível em [https://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck) . Este pacote requer que você tenha pelo menos o Visual Studio 2015 com atualização 1 instalado.  
  
 O pacote também instala outro pacote como uma dependência, uma biblioteca de suporte de diretrizes somente de cabeçalho (GSL). O GSL também está disponível no GitHub em [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) .  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Habilitar as diretrizes de Verificação Principal do C++ na análise de código  
 Para habilitar o Verificação Principal do C++ ferramentas de análise de código, instale o pacote NuGet Microsoft. CppCoreCheck em cada projeto C++ que você deseja verificar no Visual Studio.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>Para adicionar o pacote Microsoft. CppCoreCheck ao seu projeto  
  
1. No **Gerenciador de soluções**, clique com o botão direito do mouse para abrir o menu de contexto do seu projeto na solução à qual você deseja adicionar o pacote. Escolha **gerenciar pacotes NuGet** para abrir o **Gerenciador de pacotes NuGet**.  
  
2. Na janela **Gerenciador de pacotes NuGet** , procure Microsoft. CppCoreCheck.  
  
    ![Janela do Gerenciador de pacotes NuGet mostra o pacote CppCoreCheck](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. Selecione o pacote Microsoft. CppCoreCheck e, em seguida, escolha o botão **instalar** para adicionar as regras ao seu projeto.  
  
   O pacote NuGet adiciona um arquivo MSBuild. targets adicional ao seu projeto que é invocado quando você habilita a análise de código em seu projeto. Esse arquivo. targets adiciona as regras de Verificação Principal do C++ como uma extensão adicional à ferramenta de análise de código do Visual Studio.  
  
   Você pode habilitar a análise de código em seu projeto marcando a caixa de seleção **Habilitar análise de código no Build** na seção **análise de código** da caixa de diálogo **páginas de propriedades** do seu projeto.  
  
   ![Página de propriedades para configurações gerais de análise de código](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   As regras de Verificação Principal do C++ se tornam parte dos conjuntos de regras padrão que são executados quando a análise de código está habilitada. Como as regras de Verificação Principal do C++ estão em desenvolvimento, algumas regras podem não estar prontas para uso em todo o código, mas podem ser informativas durante o desenvolvimento. Essas regras são lançadas como experimentais. Você pode escolher se deseja executar as regras de lançamento ou experimental nas propriedades do seu projeto.  
  
   ![Página de propriedades para configurações de extensões de análise de código](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   Para habilitar ou desabilitar os conjuntos de regras de Verificação Principal do C++, abra a caixa de diálogo **páginas de propriedades** do seu projeto. Em **Propriedades de configuração**, expanda  **análise de código**, **extensões**. No controle suspenso ao lado de **habilitar verificação principal do C++ (liberado)** ou **Habilitar verificação principal do C++ (experimental)**, escolha **Sim** ou **não**. Escolha **OK** ou **aplicar** para salvar suas alterações.  
  
## <a name="check-types-bounds-and-lifetimes"></a>Verificar tipos, limites e tempos de vida  
 O pacote de Verificação Principal do C++ atualmente contém verificadores para a [segurança de tipo](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), segurança de [limites](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds)e perfis de segurança de [tempo de vida](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) .  
  
 Veja um exemplo do tipo de problema que as regras de Verificação Principal do C++ podem encontrar:  
  
```cpp  
// CoreCheckExample.cpp  
// Add CppCoreCheck package and enable code analysis in build for warnings.  
  
int main()  
{  
    int arr[10];           // warning C26494  
    int* p = arr;          // warning C26485  
  
    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1  
    {  
        int* q = p + 1;    // warning C26481 (suppressed)  
        p = q++;           // warning C26481 (suppressed)  
    }  
  
    return 0;  
}  
```  
  
 Este exemplo demonstra alguns dos avisos que as regras de Verificação Principal do C++ podem encontrar:  
  
- C26494 é o tipo de regra. 5: sempre inicializar um objeto.  
  
- C26485 é associado à regra. 3: nenhum decaimento de matriz para ponteiro.  
  
- C26481 são limites de regra. 1: não use aritmética de ponteiro. Use `span` em seu lugar.  
  
  Se os conjuntos de regras de análise de código Verificação Principal do C++ estiverem instalados e habilitados quando você compilar esse código, os dois primeiros avisos serão gerados, mas o terceiro será suprimido. Aqui está a saída da compilação do código de exemplo:  
  
**1> compilação de------iniciada: Projeto: CoreCheckExample, configuração: Depurar Win32--**  
**----**  
**1> CoreCheckExample. cpp**  
**1> CoreCheckExample. vcxproj-> C:\Users\username\documents\visual Studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1> CoreCheckExample. vcxproj-> C:\Users\username\documents\visual Studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (PDB completo)**  
**c:\users\username\documents\visual Studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (6): aviso C26494: a variável ' arr ' é uninitializ**  
**comandos. Sempre inicializar um objeto. (Type. 5: https: \/ /go.Microsoft.com/fwlink/p/?link**  
**ID = 620421)**  
**c:\users\username\documents\visual Studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (7): aviso C26485: expressão ' arr ': nenhuma matriz para**  
**ponteiro decaimento. (Bounds. 3: https: \/ /go.Microsoft.com/fwlink/p/?LinkId=620415)**  
**========== Compilação: 1 com êxito, 0 com falha, 0 atualizada, 0 ignorada ==========** 

As Diretrizes Principais do C++ existem para ajudá-lo a escrever um código melhor e mais seguro. No entanto, se você tiver uma instância em que uma regra ou um perfil não deve ser aplicado, será fácil suprimir diretamente no código. Você pode usar o `gsl::suppress` atributo para manter verificação principal do C++ de detectar e relatar qualquer violação de uma regra no bloco de código a seguir. Você pode marcar instruções individuais para suprimir regras específicas. Você pode até mesmo suprimir todo o perfil de limites escrevendo `[[gsl::suppress(bounds)]]` sem incluir um número de regra específico.  
  
## <a name="use-the-guideline-support-library"></a>Usar a biblioteca de suporte de diretrizes  
 O pacote NuGet Microsoft. CppCoreCheck também instala um pacote que contém a implementação da Microsoft da biblioteca de suporte de diretrizes (GSL). O GSL também está disponível no formato autônomo em [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl) . Essa biblioteca será útil se você quiser seguir as diretrizes básicas. O GSL inclui definições que permitem que você substitua construções propensas a erros com alternativas mais seguras. Por exemplo, você pode substituir um `T*, length` par de parâmetros pelo `span<T>` tipo. O GSL é um software livre, portanto, se você quiser dar uma olhada nas fontes de biblioteca, no comentário ou no Contribute, o projeto pode ser encontrado em [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) .

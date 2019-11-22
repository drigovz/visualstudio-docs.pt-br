---
title: Usando os C++ verificadores de diretrizes principais | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: ccc44b77c4524e7d707ce3fe407d204d729017ff
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74291243"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Usando os verificadores de Diretrizes Principais do C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

As C++ diretrizes básicas são um conjunto portátil de diretrizes, regras e práticas recomendadas sobre a codificação C++ criada por C++ especialistas e designers.  O Visual Studio agora dá suporte a pacotes de suplemento que criam regras adicionais para as ferramentas de análise de código para verificar seu código C++ quanto à conformidade com as diretrizes básicas e sugerir melhorias.  
  
## <a name="the-c-core-guidelines-project"></a>O C++ projeto de diretrizes principais  
 Criado por Bjarne Stroustrup e outros, as C++ principais diretrizes são um guia para usar o C++ moderno de forma segura e eficaz. As diretrizes enfatizam a segurança de tipo estático e a segurança de recursos. Eles identificam maneiras de eliminar ou minimizar as partes mais propensas a erros da linguagem e sugerem como tornar seu código mais simples e mais funcional de maneira confiável. Essas diretrizes são mantidas pela Standard C++ Foundation. Para saber mais, confira a documentação, C++ [ C++ as diretrizes básicas](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)e acesse os arquivos de projeto de documentação das diretrizes principais no [GitHub](https://github.com/isocpp/CppCoreGuidelines).  
  
 A Microsoft dá C++ suporte ao esforço das principais C++ diretrizes fazendo os conjuntos de regras de análise de código de verificação de núcleo que você pode adicionar aos seus projetos usando um pacote NuGet. O pacote é denominado Microsoft. CppCoreCheck e está disponível em [https://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck). Este pacote requer que você tenha pelo menos o Visual Studio 2015 com atualização 1 instalado.  
  
 O pacote também instala outro pacote como uma dependência, uma biblioteca de suporte de diretrizes somente de cabeçalho (GSL). O GSL também está disponível no GitHub em [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Habilitar as C++ diretrizes de verificação principal na análise de código  
 Para habilitar as C++ ferramentas de análise de código de verificação principal, instale o pacote NuGet Microsoft. C++ CppCoreCheck em cada projeto que você deseja verificar no Visual Studio.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>Para adicionar o pacote Microsoft. CppCoreCheck ao seu projeto  
  
1. No **Gerenciador de soluções**, clique com o botão direito do mouse para abrir o menu de contexto do seu projeto na solução à qual você deseja adicionar o pacote. Escolha **gerenciar pacotes NuGet** para abrir o **Gerenciador de pacotes NuGet**.  
  
2. Na janela **Gerenciador de pacotes NuGet** , procure Microsoft. CppCoreCheck.  
  
    ![Janela do Gerenciador de pacotes NuGet mostra o pacote CppCoreCheck](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. Selecione o pacote Microsoft. CppCoreCheck e, em seguida, escolha o botão **instalar** para adicionar as regras ao seu projeto.  
  
   O pacote NuGet adiciona um arquivo MSBuild. targets adicional ao seu projeto que é invocado quando você habilita a análise de código em seu projeto. Esse arquivo. targets adiciona C++ as regras de verificação principal como uma extensão adicional à ferramenta de análise de código do Visual Studio.  
  
   Você pode habilitar a análise de código em seu projeto marcando a caixa de seleção **Habilitar análise de código no Build** na seção **análise de código** da caixa de diálogo **páginas de propriedades** do seu projeto.  
  
   ![Página de propriedades para configurações gerais de análise de código](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   As C++ regras de verificação principal se tornam parte dos conjuntos de regras padrão que são executados quando a análise de código está habilitada. Como as C++ regras de verificação principais estão em desenvolvimento, algumas regras podem não estar prontas para uso em todo o código, mas podem ser informativas durante o desenvolvimento. Essas regras são lançadas como experimentais. Você pode escolher se deseja executar as regras de lançamento ou experimental nas propriedades do seu projeto.  
  
   ![Página de propriedades para configurações de extensões de análise de código](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   Para habilitar ou desabilitar os C++ conjuntos de regras de verificação principal, abra a caixa de diálogo **páginas de propriedades** do seu projeto. Em **Propriedades de configuração**, expanda **análise de código**, **extensões**. No controle suspenso ao lado de **habilitar C++ verificação de núcleo (liberado)** ou **habilitar C++ verificação de núcleo (experimental)** , escolha **Sim** ou **não**. Escolha **OK** ou **aplicar** para salvar suas alterações.  
  
## <a name="check-types-bounds-and-lifetimes"></a>Verificar tipos, limites e tempos de vida  
 O C++ pacote de verificação principal atualmente contém verificadores para a [segurança de tipo](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), segurança de [limites](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds)e perfis de segurança de [tempo de vida](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) .  
  
 Veja um exemplo do tipo de problema que as regras de C++ verificação principais podem encontrar:  
  
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
  
 Este exemplo demonstra alguns dos avisos que as regras de C++ verificação principais podem encontrar:  
  
- C26494 é o tipo de regra. 5: sempre inicializar um objeto.  
  
- C26485 é associado à regra. 3: nenhum decaimento de matriz para ponteiro.  
  
- C26481 são limites de regra. 1: não use aritmética de ponteiro. Use `span` em seu lugar.  
  
  Se os C++ conjuntos de regras de análise de código de verificação principal estiverem instalados e habilitados quando você compilar esse código, os dois primeiros avisos serão gerados, mas o terceiro será suprimido. Aqui está a saída da compilação do código de exemplo:  
  
**1 > compilação de------iniciada: Projeto: CoreCheckExample, configuração: Depurar Win32--**  
**----**  
**1 > CoreCheckExample. cpp**  
**1 > CoreCheckExample. vcxproj-> C:\Users\username\documents\visual Studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1 > CoreCheckExample. vcxproj-> C:\Users\username\documents\visual Studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (PDB completo)**  
**c:\users\username\documents\visual Studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (6): aviso C26494: a variável ' arr ' é uninitializ**  
**Ed. sempre inicializar um objeto. (Type. 5: https://go.microsoft.com/fwlink/p/?Link**  
**ID=620421)**  
**c:\users\username\documents\visual Studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (7): aviso C26485: expressão ' arr ': nenhuma matriz para**  
**ponteiro decaimento. (limites. 3: https://go.microsoft.com/fwlink/p/?LinkID=620415)**  
= = = = = = = = = = **Compilação: 1 com êxito, 0 com falha, 0 atualizado, 0 ignorado = =** = = = = = = = = = As C++ diretrizes básicas estão lá para ajudá-lo a escrever um código melhor e mais seguro. No entanto, se você tiver uma instância em que uma regra ou um perfil não deve ser aplicado, será fácil suprimir diretamente no código. Você pode usar o atributo `gsl::suppress` para impedir C++ que a verificação principal detecte e relate qualquer violação de uma regra no bloco de código a seguir. Você pode marcar instruções individuais para suprimir regras específicas. Você pode até mesmo suprimir todo o perfil de limites escrevendo `[[gsl::suppress(bounds)]]` sem incluir um número de regra específico.  
  
## <a name="use-the-guideline-support-library"></a>Usar a biblioteca de suporte de diretrizes  
 O pacote NuGet Microsoft. CppCoreCheck também instala um pacote que contém a implementação da Microsoft da biblioteca de suporte de diretrizes (GSL). O GSL também está disponível no formato autônomo em [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl). Essa biblioteca será útil se você quiser seguir as diretrizes básicas. O GSL inclui definições que permitem que você substitua construções propensas a erros com alternativas mais seguras. Por exemplo, você pode substituir um `T*, length` par de parâmetros pelo tipo de `span<T>`. O GSL é um software livre, portanto, se você quiser dar uma olhada nas fontes de biblioteca, no comentário ou no Contribute, o projeto pode ser encontrado em [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).

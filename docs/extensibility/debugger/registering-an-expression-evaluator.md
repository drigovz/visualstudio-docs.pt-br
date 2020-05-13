---
title: Registrando um Avaliador de Expressão | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 600f7c8a2e2957cddf23ccc82b0872617e491940
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713206"
---
# <a name="register-an-expression-evaluator"></a>Registre um avaliador de expressão
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 O avaliador de expressão (EE) deve registrar-se como uma fábrica de classes com o ambiente Windows COM e visual studio. Um EE é configurado como um DLL para que seja injetado no espaço de endereço do mecanismo de depuração (DE) ou no espaço de endereço do Visual Studio, dependendo de qual entidade instancia o EE.

## <a name="managed-code-expression-evaluator"></a>Avaliador gerenciado de expressão de código
 Um código gerenciado EE é implementado como uma Biblioteca de Classe, que é uma DLL que se registra no ambiente COM, normalmente iniciada por uma chamada para o programa VSIP, *regpkg.exe*. O processo real de escrever as chaves de registro para o ambiente COM é tratado automaticamente.

 Um método da classe principal <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>é marcado com , indicando que o método deve ser chamado quando a DLL está sendo registrada com COM. Este método de `RegisterClass`registro, muitas vezes chamado, executa a tarefa de registrar o DLL com o Visual Studio. Um `UnregisterClass` correspondente (marcado <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>com o ), `RegisterClass` desfaz os efeitos de quando a DLL é desinstalada.
As mesmas entradas de registro são feitas como para um EE escrito em código não gerenciado; a única diferença é que não há `SetEEMetric` função de ajudante, como fazer o trabalho para você. A seguir está um exemplo do processo de registro e descadastramento.

### <a name="example"></a>Exemplo
 A função a seguir mostra como um Código Gerenciado EE registra e não se registra no Visual Studio.

```csharp
namespace EEMC
{
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]
    public class EEMCClass : IDebugExpressionEvaluator
    {
        #region Register and unregister.
        private static Guid guidMycLang = new Guid("462D4A3E-B257-4AEE-97CD-5918C7531757");
        private static string languageName = "MyC";
        private static string eeName = "MyC Expression Evaluator";

        private static Guid guidMicrosoftVendor = new Guid("994B45C4-E6E9-11D2-903F-00C04FA302A1");
        private static Guid guidCOMPlusOnlyEng = new Guid("449EC4CC-30D2-4032-9256-EE18EB41B62B");
        private static Guid guidCOMPlusNativeEng = new Guid("92EF0900-2251-11D2-B72E-0000F87572EF");

        /// <summary>
        /// Register the expression evaluator.
        /// Set "project properties/configuration properties/build/register for COM interop" to true.
        /// </summary>
         [ComRegisterFunctionAttribute]
        public static void RegisterClass(Type t)
        {
            // Get Visual Studio version (set by regpkg.exe)
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");
            string s = @"SOFTWARE\Microsoft\VisualStudio\"
                        + hive
                        + @"\AD7Metrics\ExpressionEvaluator";

            RegistryKey rk = Registry.LocalMachine.CreateSubKey(s);
            if (rk == null)  return;

            rk = rk.CreateSubKey(guidMycLang.ToString("B"));
            rk = rk.CreateSubKey(guidMicrosoftVendor.ToString("B"));
            rk.SetValue("CLSID", t.GUID.ToString("B"));
            rk.SetValue("Language", languageName);
            rk.SetValue("Name", eeName);

            rk = rk.CreateSubKey("Engine");
            rk.SetValue("0", guidCOMPlusOnlyEng.ToString("B"));
            rk.SetValue("1", guidCOMPlusNativeEng.ToString("B"));
        }
        /// <summary>
        /// Unregister the expression evaluator.
        /// </summary>
         [ComUnregisterFunctionAttribute]
        public static void UnregisterClass(Type t)
        {
            // Get Visual Studio version (set by regpkg.exe)
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");
            string s = @"SOFTWARE\Microsoft\VisualStudio\"
                        + hive
                        + @"\AD7Metrics\ExpressionEvaluator\"
                        + guidMycLang.ToString("B");
            RegistryKey key = Registry.LocalMachine.OpenSubKey(s);
            if (key != null)
            {
                key.Close();
                Registry.LocalMachine.DeleteSubKeyTree(s);
            }
        }
    }
}
```

## <a name="unmanaged-code-expression-evaluator"></a>Avaliador de expressão de código não gerenciado
 O EE DLL `DllRegisterServer` implementa a função para registrar-se no ambiente COM, bem como no Visual Studio.

> [!NOTE]
> Você pode encontrar o código de registro de amostra de código MyCEE no arquivo *dllentry.cpp*, que está localizado na instalação VSIP em EnVSDK\MyCPkgs\MyCEE.

### <a name="dll-server-process"></a>Processo do servidor DLL
 Ao registrar o EE, o servidor DLL:

1. Registra sua fábrica `CLSID` de classe de acordo com convenções com normais.

2. Chama a função `SetEEMetric` auxiliar para registrar no Visual Studio as métricas EE mostradas na tabela a seguir. A `SetEEMetric` função e as métricas especificadas a seguir fazem parte da biblioteca *dbgmetric.lib.* Consulte [os ajudantes do SDK para depurar](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) detalhes.

    |Métrica|Descrição|
    |------------|-----------------|
    |`metricCLSID`|`CLSID`da fábrica de classe EE|
    |`metricName`|Nome do EE como uma seqüência de string exibivel|
    |`metricLanguage`|O nome da linguagem que o EE foi projetado para avaliar|
    |`metricEngine`|`GUID`s dos motores de depuração (DE) que trabalham com este EE|

    > [!NOTE]
    > O `metricLanguage``GUID` identifica o idioma pelo nome, `guidLang` mas `SetEEMetric` é o argumento para que seleciona o idioma. Quando o compilador gera o arquivo de informações `guidLang` de depuração, ele deve escrever o apropriado para que o DE saiba qual EE usar. O DE normalmente pede ao `GUID`provedor de símbolos esse idioma , que é armazenado no arquivo de informações de depuração.

3. Registra-se no Visual Studio criando chaves em HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, onde *x.Y* é a versão do Visual Studio para se registrar.

### <a name="example"></a>Exemplo
 A função a seguir mostra como um Código não gerenciado (C++) EE registra e não se registra no Visual Studio.

```cpp
/*---------------------------------------------------------
  Registration
-----------------------------------------------------------*/
#ifndef LREGKEY_VISUALSTUDIOROOT
    #define LREGKEY_VISUALSTUDIOROOT L"Software\\Microsoft\\VisualStudio\\8.0"
#endif

static HRESULT RegisterMetric( bool registerIt )
{
    // check where we should register
    const ULONG cchBuffer = _MAX_PATH;
    WCHAR wszRegistrationRoot[cchBuffer];
    DWORD cchFreeBuffer = cchBuffer - 1;
    wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT_NOVERSION);
    wcscat(wszRegistrationRoot, L"\\");

    // this is Environment SDK specific
    // we check for  EnvSdk_RegKey environment variable to
    // determine where to register
    DWORD cchDefRegRoot = lstrlenW(LREGKEY_VISUALSTUDIOROOT_NOVERSION) + 1;
    cchFreeBuffer = cchFreeBuffer - cchDefRegRoot;
    DWORD cchEnvVarRead = GetEnvironmentVariableW(
        /* LPCTSTR */ L"EnvSdk_RegKey", // environment variable name
        /* LPTSTR  */ &wszRegistrationRoot[cchDefRegRoot],// buffer for variable value
        /* DWORD   */ cchFreeBuffer);// size of buffer
    if (cchEnvVarRead >= cchFreeBuffer)
        return E_UNEXPECTED;
    // If the environment variable does not exist then we must use
    // LREGKEY_VISUALSTUDIOROOT which has the version number.
    if (0 == cchEnvVarRead)
        wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT);

    if (registerIt)
    {
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricCLSID,
                    CLSID_MycEE,
                    wszRegistrationRoot );
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricName,
                    GetString(IDS_INFO_MYCDESCRIPTION),
                    wszRegistrationRoot );
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricLanguage, L"MyC",
                    wszRegistrationRoot);

        GUID engineGuids[2];
        engineGuids[0] = guidCOMPlusOnlyEng;
        engineGuids[1] = guidCOMPlusNativeEng;
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricEngine,
                    engineGuids,
                    2,
                    wszRegistrationRoot);
    }
    else
    {
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricCLSID,
                        wszRegistrationRoot);
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricName,
                        wszRegistrationRoot );
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricLanguage,
                        wszRegistrationRoot );
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricEngine,
                        wszRegistrationRoot );
    }

    return S_OK;
}
```

## <a name="see-also"></a>Confira também
- [Escrevendo um avaliador de expressão CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Auxiliares SDK para depuração](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

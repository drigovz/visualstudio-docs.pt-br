---
title: Fazendo com que os projetos personalizados reconheçam a versão | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 5233d3ff-6e89-4401-b449-51b4686becca
caps.latest.revision: 33
manager: jillfra
ms.openlocfilehash: 0b29728cffc962b5d09a5adc45f8cac2093b020a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825678"
---
# <a name="making-custom-projects-version-aware"></a>Tornando projetos personalizados com reconhecimento de versão
No sistema de projeto personalizado, você pode permitir que projetos desse tipo sejam carregados em várias versões do Visual Studio. Você também pode impedir que projetos desse tipo sejam carregados em uma versão anterior do Visual Studio. Você também pode habilitar esse projeto para se identificar para uma versão posterior, caso o projeto exija reparo, conversão ou reprovação.  
  
## <a name="allowing-projects-to-load-in-multiple-versions"></a>Permitindo que os projetos sejam carregados em várias versões  
 Você pode modificar a maioria dos projetos que foram criados no [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] com SP1 ou posterior para trabalhar em várias versões.  
  
 Antes de um projeto ser carregado, o Visual Studio chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> método para determinar se o projeto pode ser atualizado. Se o projeto puder ser atualizado, o `UpgradeProject_CheckOnly` método definirá um sinalizador que causa uma chamada posterior ao <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método para atualizar o projeto. Como os projetos incompatíveis não podem ser atualizados, `UpgradeProject_CheckOnly` o deve primeiro verificar a compatibilidade do projeto, conforme descrito na seção anterior.  
  
 Você, como autor de um sistema de projeto, implementa `UpgradeProject_CheckOnly` (da `IVsProjectUpgradeViaFactory4` interface) para fornecer aos usuários de seu sistema de projeto uma verificação de atualização. Quando os usuários abrem um projeto, esse método é chamado para determinar se um projeto deve ser reparado antes de ser carregado. Os requisitos de atualização possíveis são enumerados em `VSPUVF_REPAIRFLAGS` e incluem as seguintes possibilidades:  
  
1. `SPUVF_PROJECT_NOREPAIR`: Não requer reparo.  
  
2. `VSPUVF_PROJECT_SAFEREPAIR`: Torna o projeto compatível com uma versão anterior sem os problemas que você pode ter encontrado com as versões anteriores do produto.  
  
3. `VSPUVF_PROJECT_UNSAFEREPAIR`: O torna o projeto compatível com versões anteriores, mas com algum risco dos problemas que você pode ter encontrado com a versão anterior do produto. Por exemplo, o projeto não será compatível se ele depender de versões diferentes do SDK.  
  
4. `VSPUVF_PROJECT_ONEWAYUPGRADE`: Torna o projeto incompatível com uma versão anterior.  
  
5. `VSPUVF_PROJECT_INCOMPATIBLE`: Indica que a versão atual não dá suporte a este projeto.  
  
6. `VSPUVF_PROJECT_DEPRECATED`: Indica que não há mais suporte para este projeto.  
  
> [!NOTE]
> Para evitar confusão, não Combine sinalizadores de atualização ao defini-los. Por exemplo, não crie um status de atualização ambíguo, como `VSPUVF_PROJECT_SAFEREPAIR | VSPUVF_PROJECT_DEPRECATED` .  
  
 Os tipos de projeto podem implementar a função `UpgradeProjectFlavor_CheckOnly` da `IVsProjectFlavorUpgradeViaFactory2` interface. Para que essa função funcione, a `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly` implementação mencionada anteriormente deve chamá-la. Essa chamada já está implementada no sistema de projeto base Visual Basic ou C#. O efeito dessa função permite que os tipos de projeto também determinem os requisitos de atualização de um projeto, além do que o sistema de projeto base determina. A caixa de diálogo compatibilidade mostra os dois requisitos mais graves.  
  
 Quando o Visual Studio executa uma verificação de atualização, ele fornece um agente em vez de um valor nulo como nas versões anteriores do Visual Studio. O agente permite que os sistemas de projeto e os tipos forneçam informações adicionais que podem ajudá-lo a entender a natureza das alterações necessárias para fazer com que seus projetos mais antigos sejam carregados corretamente. Recomendamos que você use o agente para fornecer mais informações em vez de usar caixas de diálogo. Para obter mais informações, consulte [o atualizar o agente de log](../misc/making-custom-projects-version-aware.md#BKMK_UpgradeLogger) mais adiante neste tópico.  
  
 Para implementações gerenciadas, as interfaces de atualização de projeto estão disponíveis no assembly de interoperabilidade Microsoft.VisualStudio.Shell.Interop.11.0.dll.  
  
 O `UpgradeProject` método pode determinar se as alterações feitas por ele impedirão que o projeto fosse carregado em uma versão anterior do Visual Studio. Nesse caso, o método marca o projeto como incompatível. Para entender como um projeto é marcado como incompatível, consulte [marcando um projeto como incompatível](../misc/making-custom-projects-version-aware.md#BKMK_Incompat) anteriormente neste tópico. É recomendável que, depois que essa caixa de diálogo for exibida, você marque o projeto como incompatível chamando o método `IVsAppCompat.BreakAssetCompatibility` diretamente, em vez de chamar primeiro o `IVsAppCompat.AskForUserConsentToBreakAssetCompat` método, pois a caixa de diálogo não precisa aparecer duas vezes.  
  
 Aqui está um exemplo para ajudar a resumir a experiência do usuário de compatibilidade. Se um projeto tiver sido criado em uma versão anterior e a versão atual determinar que uma atualização é necessária, o Visual Studio exibirá uma caixa de diálogo para pedir ao usuário permissão para fazer as alterações. Se o usuário concordar, o projeto será modificado e, em seguida, carregado. Se a solução for fechada e reaberta na versão anterior, o projeto de atualização unidirecional será incompatível e não carregado. Se o projeto precisar apenas de um reparo (em vez de uma atualização), o projeto reparado ainda será aberto em ambas as versões.  
  
## <a name="marking-a-project-as-incompatible"></a><a name="BKMK_Incompat"></a> Marcando um projeto como incompatível  
 Você pode marcar um projeto como incompatível com as versões anteriores do Visual Studio.  Por exemplo, suponha que você crie um projeto que usa um recurso .NET Framework 4,5. Como este projeto não pode ser criado [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] , você pode marcá-lo como incompatível para impedir que essa versão tente carregá-la.  
  
 O componente que adiciona o recurso incompatível é responsável por marcar o projeto como incompatível. O componente deve ter acesso à <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface que representa os projetos de interesse.  
  
#### <a name="to-mark-a-project-as-incompatible"></a>Para marcar um projeto como incompatível  
  
1. No componente, obtenha uma `IVsAppCompat` interface do serviço global SVsSolution.  
  
     Para obter mais informações, consulte <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>.  
  
2. No componente, chame `IVsAppCompat.AskForUserConsentToBreakAssetCompat` e transmita a ele uma matriz de `IVsHierarchy` interfaces que representam os projetos de seu interesse.  
  
     Esse método tem a seguinte assinatura:  
  
    ```  
    HRESULT AskForUserConsentToBreakAssetCompat([in] SAFEARRAY(IVsHierarchy*) sarrProjectHierarchies)  
  
    ```  
  
     Se você implementar esse código, uma caixa de diálogo compatibilidade de projeto será exibida. A caixa de diálogo solicitará ao usuário a permissão para marcar todos os projetos especificados como incompatíveis. Se o usuário concordar, `AskForUserConsentToBreakAssetCompat` retorna `S_OK` ; caso contrário, `AskForUserConsentToBreakAssetCompat` retorna `OLE_E_PROMPTSAVECANCELLED` .  
  
    > [!WARNING]
    > Na maioria dos cenários comuns, a matriz conterá `IVsHierarchy` apenas um item.  
  
3. Se `AskForUserConsentToBreakAssetCompat` retorna `S_OK` , o componente faz ou aceita as alterações que interrompem a compatibilidade.  
  
4. Em seu componente, chame o `IVsAppCompat.BreakAssetCompatibility` método para cada projeto que você deseja marcar como incompatível. O componente pode definir o valor do parâmetro `lpszMinimumVersion` para uma versão mínima específica, em vez de fazer com que o Visual Studio procure a cadeia de caracteres da versão atual no registro. Essa abordagem minimiza o risco do componente de definir inadvertidamente um valor mais alto no futuro, com base no que está no registro naquele momento. Se esse valor mais alto tiver sido definido, o Visual Studio não pôde abrir o projeto.  
  
     Esse método tem a seguinte assinatura:  
  
    ```  
    HRESULT BreakAssetCompatibility([in] IVsHierarchy * pProjHier), [in] LPCOLESTR lpszMinimumVersion);  
  
    ```  
  
     Se o componente definir `lpszMinimumVersion` como NULL, o `BreakAssetCompatibility` método chamará o `IVsAppCompat.GetCurrentDesignTimeCompatVersion` método para obter uma cadeia de caracteres que representa a versão atual do Visual Studio.  
  
     Esse método tem a seguinte assinatura:  
  
    ```  
    HRESULT GetCurrentDesignTimeCompatVersion([out] BSTR * pbstrCurrentDesignTimeCompatVersion)  
    ```  
  
     O método BreakAssetCompatibility então chama o `IVsHierarchy.SetProperty` método para definir a `VSHPROPID_MinimumDesignTimeCompatVersion` Propriedade root como o valor da cadeia de caracteres de versão que você obteve na etapa anterior.  
  
     Para obter mais informações, consulte <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  
  
> [!IMPORTANT]
> Você deve implementar a `VSHPROPID_MinimumDesignTimeCompatVersion` propriedade para marcar um projeto como compatível ou incompatível. Por exemplo, se o sistema do projeto usar um arquivo de projeto do MSBuild, adicione ao arquivo de projeto uma `<MinimumVisualStudioVersion>` propriedade de compilação que tenha um valor igual ao `VSHPROPID_MinimumDesignTimeCompatVersion` valor da propriedade correspondente.  
  
## <a name="detecting-whether-a-project-is-incompatible"></a>Detectando se um projeto é incompatível  
 Um projeto que é incompatível com a versão atual do Visual Studio deve ser mantido no carregamento. Além disso, um projeto incompatível não pode ser atualizado ou reparado. Portanto, um projeto deve ser verificado quanto à compatibilidade duas vezes: primeiro, quando ele está sendo considerado para atualização ou reparo, e segundo, antes de ser carregado.  
  
 Para habilitar a detecção de incompatibilidade de projeto, você deve implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> os <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> métodos e. Se um projeto for incompatível, `UpgradeProject_CheckOnly` o deverá retornar o código de êxito `VS_S_INCOMPATIBLEPROJECT` e `CreateProject` deverá retornar o código de erro `VS_E_INCOMPATIBLEPROJECT` . Para projetos do tipo, você deve implementar `IVsProjectFlavorUpgradeViaFactory2.UpgradeProjectFlavor_CheckOnly` em vez de `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly` .  
  
 Um sistema de projeto é referido como indicado se ele tiver uma Web, um Office (VSTO), um Silverlight ou outro tipo de projeto criado com base nele. Sistemas de projeto mais antigos que já implementam `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` e sistemas de projeto reprojetados que já implementam `IVsProjectFlavorUpgradeViaFactory.UpgradeProjectFlavor_CheckOnly` continuam com suporte. A versão mais antiga do `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` tem a seguinte assinatura de implementação:  
  
```  
IVsProjectUpgradeViaFactory::UpgradeProject_CheckOnly(  
  
/* [in] */ BSTR bstrFileName,  
/* [in] */ IVsUpgradeLogger *pLogger,  
/* [out] */ BOOL *pUpgradeRequired,  
/* [out] */ GUID *pguidNewProjectFactory,  
/* [out] */ VSPUVF_FLAGS *pUpgradeProjectCapabilityFlags  
)  
```  
  
 Se esse método definir `pUpgradeRequired` como true e retornar `S_OK` , o resultado será tratado como "upgrade" e, como se o método definir um sinalizador de atualização para o valor `VSPUVF_PROJECT_ONEWAYUPGRADE` , que será descrito posteriormente neste tópico. Os valores de retorno a seguir têm suporte usando esse método mais antigo, mas somente quando `pUpgradeRequired` é definido como true:  
  
1. `VS_S_PROJECT_SAFEREPAIRREQUIRED`. Esse valor de retorno converte o `pUpgradeRequired` valor como true como equivalente a `VSPUVF_PROJECT_SAFEREPAIR` , que é descrito posteriormente neste tópico.  
  
2. `VS_S_PROJECT_UNSAFEREPAIRREQUIRED`. Esse valor de retorno converte o `pUpgradeRequired` valor como true como equivalente a `VSPUVF_PROJECT_UNSAFEREPAIR` , que é descrito posteriormente neste tópico  
  
3. `VS_S_PROJECT_ONEWAYUPGRADEREQUIRED`. Esse valor de retorno converte o `pUpgradeRequired` valor como true como equivalente a `VSPUVF_PROJECT_ONEWAYUPGRADE` , que é descrito posteriormente neste tópico.  
  
   As novas implementações no `IVsProjectUpgradeViaFactory4` e `IVsProjectFlavorUpgradeViaFactory2` habilitam a especificação do tipo de migração com mais precisão.  
  
> [!NOTE]
> Você pode armazenar em cache o resultado da verificação de compatibilidade pelo `UpgradeProject_CheckOnly` método para que ele também possa ser usado pela chamada subsequente para `CreateProject` .  
  
 Por exemplo, se os `UpgradeProject_CheckOnly` `CreateProject` métodos e que são gravados para um [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] sistema de projeto do com SP1 examinam um arquivo de projeto e acham que a `<MinimumVisualStudioVersion>` propriedade de compilação é "11,0", o Visual Studio 2010 com SP1 não carregará o projeto. Além disso, o **navegador de soluções** indicaria que o projeto é "incompatível" e não o carregará.  
  
## <a name="the-upgrade-logger"></a><a name="BKMK_UpgradeLogger"></a> O agente de atualização  
 A chamada para `IVsProjectUpgradeViaFactory::UpgradeProject` contém um `IVsUpgradeLogger` agente de log, que os sistemas de projeto e os tipos devem usar para fornecer um rastreamento detalhado de atualização para solução de problemas. Se um aviso ou um erro for registrado, o Visual Studio mostrará o relatório de atualização.  
  
 Ao gravar no agente de atualização, considere as seguintes diretrizes:  
  
- O Visual Studio chamará flush após a conclusão da atualização de todos os projetos. Não o chame em seu sistema de projeto.  
  
- A função LogMessage tem os seguintes ErrorLevels:  
  
  - 0 é para todas as informações que você gostaria de rastrear.  

  - 1 é para um aviso.  

  - 2 é um erro  

  - 3 é para o formatador de relatório. Quando o projeto for atualizado, registre a palavra "convertida" uma vez e não localize a palavra.  
  
- Se um projeto não exigir reparo ou atualização, o Visual Studio irá gerar o arquivo de log somente se o sistema do projeto tiver registrado um aviso ou um erro durante UpgradeProject_CheckOnly ou UpgradeProjectFlavor_CheckOnly métodos.

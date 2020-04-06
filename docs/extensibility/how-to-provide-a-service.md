---
title: 'Como: Fornecer um Serviço | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60cae5e8048a0234114e1f9e7d97728e26ee40f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710780"
---
# <a name="how-to-provide-a-service"></a>Como: Fornecer um serviço
Um VSPackage pode fornecer serviços que outros VSPackages podem usar. Para fornecer um serviço, um VSPackage deve registrar o serviço no Visual Studio e adicionar o serviço.

 A <xref:Microsoft.VisualStudio.Shell.Package> classe implementa ambos <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> e <xref:System.ComponentModel.Design.IServiceContainer>. <xref:System.ComponentModel.Design.IServiceContainer>contém métodos de retorno de chamada que fornecem serviços sob demanda.

 Para obter mais informações sobre serviços, consulte [Serviços essenciais](../extensibility/internals/service-essentials.md) .

> [!NOTE]
> Quando um VSPackage está prestes a ser descarregado, o Visual Studio espera até que todas as solicitações de serviços que um VSPackage fornece tenham sido entregues. Não permite novas solicitações para esses serviços. Você não deve chamar <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> explicitamente o método para revogar um serviço ao descarregar.

## <a name="implement-a-service"></a>Implementar um serviço

1. Criar um projeto VSIX (**Arquivo** > **Novo** > **Projeto** > Visual**C#** > **Extensibility** > **VSIX Project**).

2. Adicione um VSPackage ao projeto. Selecione o nó do projeto no **Solution Explorer** e clique em **Adicionar** > **novo item** > **Visual C# Items** > **Extensibility** > **Visual Studio Package**.

3. Para implementar um serviço, você precisa criar três tipos:

   - Uma interface que descreve o serviço. Muitas dessas interfaces estão vazias, ou seja, não têm métodos.

   - Uma interface que descreve a interface de serviço. Esta interface inclui os métodos a serem implementados.

   - Uma classe que implementa tanto o serviço quanto a interface de serviço.

     O exemplo a seguir mostra uma implementação básica dos três tipos. O construtor da classe de serviço deve definir o provedor de serviços.

   ```csharp
   public class MyService : SMyService, IMyService
   {
       private Microsoft.VisualStudio.OLE.Interop.IServiceProvider serviceProvider;
       private string myString;
       public MyService(Microsoft.VisualStudio.OLE.Interop.IServiceProvider sp)
       {
           Trace.WriteLine(
                  "Constructing a new instance of MyService");
           serviceProvider = sp;
       }
       public void Hello()
       {
           myString = "hello";
       }
       public string Goodbye()
       {
          return "goodbye";
       }
   }
   public interface SMyService
   {
   }
   public interface IMyService
   {
       void Hello();
       string Goodbye();
   }

   ```

### <a name="register-a-service"></a>Registre um serviço

1. Para registrar um serviço, adicione o <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> VSPackage que fornece o serviço. Veja um exemplo:

    ```csharp
    [ProvideService(typeof(SMyService))]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [Guid(VSPackage1.PackageGuidString)]
    public sealed class VSPackage1 : Package
    {. . . }
    ```

     Este atributo `SMyService` registra-se no Visual Studio.

    > [!NOTE]
    > Para registrar um serviço que substitua outro serviço <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>com o mesmo nome, use o . Note que apenas uma substituição de um serviço é permitida.

### <a name="add-a-service"></a>Adicionar um serviço

1. No inicializador VSPackage, adicione o serviço e adicione um método de retorno de chamada para criar os serviços. Aqui está a mudança <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> a fazer para o método:

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);
    . . .
    }
    ```

2. Implemente o método de retorno de chamada, que deve criar e retornar o serviço, ou nulo se ele não puder ser criado.

    ```csharp
    private object CreateService(IServiceContainer container, Type serviceType)
    {
        if (typeof(SMyService) == serviceType)
            return new MyService(this);
        return null;
    }
    ```

    > [!NOTE]
    > O Visual Studio pode rejeitar uma solicitação para fornecer um serviço. Ele faz isso se outro VSPackage já fornece o serviço.

3. Agora você pode obter o serviço e usar seus métodos. O exemplo abaixo mostra o uso do serviço no inicializador, mas você pode obter o serviço em qualquer lugar que você quiser usar o serviço.

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);

        MyService myService = (MyService) this.GetService(typeof(SMyService));
        myService.Hello();
        string helloString = myService.Goodbye();

        base.Initialize();
    }
    ```

     O valor `helloString` de deve ser "Olá".

## <a name="see-also"></a>Confira também
- [Como: Obter um serviço](../extensibility/how-to-get-a-service.md)
- [Usar e prestar serviços](../extensibility/using-and-providing-services.md)
- [Essenciais de serviço](../extensibility/internals/service-essentials.md)

---
title: GEOMETRY、GEOGRAPHY、および HIERARCHYID のクライアント側での使用に関する警告Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 500ee6b3-2154-45d2-a3cf-8760166d9413
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 66898aa056800c0a7573b5afa73762785706ff7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640370"
---
# <a name="warning-about-client-side-usage-of-geometry-geography-and-hierarchyid"></a><span data-ttu-id="13be0-102">幾何学、地理学、HIERARCHYID のクライアント側の使用に関する警告</span><span class="sxs-lookup"><span data-stu-id="13be0-102">Warning about client side usage of GEOMETRY, GEOGRAPHY and HIERARCHYID</span></span>
  <span data-ttu-id="13be0-103">空間データ型を含むアセンブリ**Microsoft.SqlServer.Types.dll**が、バージョン10.0 からバージョン11.0 にアップグレードされました。</span><span class="sxs-lookup"><span data-stu-id="13be0-103">The assembly **Microsoft.SqlServer.Types.dll**, which contains the spatial data types, has been upgraded from version 10.0 to version 11.0.</span></span> <span data-ttu-id="13be0-104">このアセンブリを参照するカスタム アプリケーションは、特定の条件に該当する場合に失敗します。</span><span class="sxs-lookup"><span data-stu-id="13be0-104">Custom applications that reference this assembly may fail when certain conditions are true.</span></span>  
  
## <a name="component"></a><span data-ttu-id="13be0-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="13be0-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="13be0-106">説明</span><span class="sxs-lookup"><span data-stu-id="13be0-106">Description</span></span>  
 <span data-ttu-id="13be0-107">空間データ型を含むアセンブリ**Microsoft.SqlServer.Types.dll**が、バージョン10.0 からバージョン11.0 にアップグレードされました。</span><span class="sxs-lookup"><span data-stu-id="13be0-107">The assembly **Microsoft.SqlServer.Types.dll**, which contains the spatial data types, has been upgraded from version 10.0 to version 11.0.</span></span> <span data-ttu-id="13be0-108">このアセンブリを参照するカスタム アプリケーションは、次の条件に該当する場合に失敗します。</span><span class="sxs-lookup"><span data-stu-id="13be0-108">Custom applications that reference this assembly may fail when the following conditions are true.</span></span>  
  
-   <span data-ttu-id="13be0-109">がインストールされているコンピューターから、がインストールされているコンピューターにカスタムアプリケーションを移動すると、参照されている [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョン10.0 の**SqlTypes**アセンブリが存在しないため、アプリケーションは失敗します。</span><span class="sxs-lookup"><span data-stu-id="13be0-109">When you move a custom application from a computer on which [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] was installed to a computer on which only [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] is installed, the application will fail because the referenced version 10.0 of the **SqlTypes** assembly is not present.</span></span> <span data-ttu-id="13be0-110">この場合、次のエラー メッセージが返されることがあります: `"Could not load file or assembly 'Microsoft.SqlServer.Types, Version=10.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The system cannot find the file specified."`</span><span class="sxs-lookup"><span data-stu-id="13be0-110">You may see this error message: `"Could not load file or assembly 'Microsoft.SqlServer.Types, Version=10.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The system cannot find the file specified."`</span></span>  
  
-   <span data-ttu-id="13be0-111">**SqlTypes**アセンブリバージョン11.0 を参照するときに、バージョン10.0 もインストールされていると、次のエラーメッセージが表示されることがあります。`"System.InvalidCastException: Unable to cast object of type 'Microsoft.SqlServer.Types.SqlGeometry' to type 'Microsoft.SqlServer.Types.SqlGeometry'."`</span><span class="sxs-lookup"><span data-stu-id="13be0-111">When you reference the **SqlTypes** assembly version 11.0, and version 10.0 is also installed, you may see this error message: `"System.InvalidCastException: Unable to cast object of type 'Microsoft.SqlServer.Types.SqlGeometry' to type 'Microsoft.SqlServer.Types.SqlGeometry'."`</span></span>  
  
-   <span data-ttu-id="13be0-112">.NET 3.5、4、または4.5 を対象とするカスタムアプリケーションから**SqlTypes**アセンブリバージョン11.0 を参照する場合、アプリケーションは失敗します。これは、の仕様では、アセンブリのバージョン10.0 が読み込まれるためです。</span><span class="sxs-lookup"><span data-stu-id="13be0-112">When you reference the **SqlTypes** assembly version 11.0 from a custom application that targets .NET 3.5, 4, or 4.5, the application will fail because SqlClient by design loads version 10.0 of the assembly.</span></span> <span data-ttu-id="13be0-113">このエラーは、アプリケーションが次のいずれかのメソッドを呼び出したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="13be0-113">This failure occurs when the application calls one of the following methods:</span></span>  
  
    -   <span data-ttu-id="13be0-114">`GetValue` クラスの `SqlDataReader` メソッド</span><span class="sxs-lookup"><span data-stu-id="13be0-114">`GetValue` method of the `SqlDataReader` class</span></span>  
  
    -   <span data-ttu-id="13be0-115">`GetValues` クラスの `SqlDataReader` メソッド</span><span class="sxs-lookup"><span data-stu-id="13be0-115">`GetValues` method of the `SqlDataReader` class</span></span>  
  
    -   <span data-ttu-id="13be0-116">`SqlDataReader` クラスの角かっこインデックス演算子 []</span><span class="sxs-lookup"><span data-stu-id="13be0-116">bracket index operator [] of the `SqlDataReader` class</span></span>  
  
    -   <span data-ttu-id="13be0-117">`ExecuteScalar` クラスの `SqlCommand` メソッド</span><span class="sxs-lookup"><span data-stu-id="13be0-117">`ExecuteScalar` method of the `SqlCommand` class</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="13be0-118">修正措置</span><span class="sxs-lookup"><span data-stu-id="13be0-118">Corrective Action</span></span>  
 <span data-ttu-id="13be0-119">この問題は、次のいずれかの方法を使用して回避できます。</span><span class="sxs-lookup"><span data-stu-id="13be0-119">You can work around this issue by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="13be0-120">この問題を回避するには、コード内で、上にリストされている Get メソッドの代わりに `GetSqlBytes` メソッドを呼び出して、CLR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム型を取得します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="13be0-120">You can work around this issue in your code by calling the `GetSqlBytes` method, instead of the Get methods listed above, to retrieve CLR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system types, as shown in the following example:</span></span>  
  
    ```csharp  
    string query = "SELECT [SpatialColumn] FROM [SpatialTable]";  
          using (SqlConnection conn = new SqlConnection("..."))  
          {  
                SqlCommand cmd = new SqlCommand(query, conn);  
  
                conn.Open();  
                SqlDataReader reader = cmd.ExecuteReader();  
  
                while (reader.Read())  
                {  
                      // In version 11.0 only  
                      SqlGeometry g =   
    SqlGeometry.Deserialize(reader.GetSqlBytes(0));  
  
                      // In version 10.0 or 11.0  
                      SqlGeometry g2 = new SqlGeometry();  
                      g.Read(new BinaryReader(reader.GetSqlBytes(0).Stream));  
                }  
          }  
    ```  
  
-   <span data-ttu-id="13be0-121">この問題を回避するには、アプリケーション構成ファイル内でアセンブリのリダイレクトを使用します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="13be0-121">You can work around this issue by using assembly redirection in the application configuration file, as shown in the following example:</span></span>  
  
    ```xml  
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
        ...  
        <dependentAssembly>  
            <assemblyIdentity name="Microsoft.SqlServer.Types" publicKeyToken="89845dcd8080cc91" culture="neutral" />  
            <bindingRedirect oldVersion="10.0.0.0" newVersion="11.0.0.0" />  
        </dependentAssembly>  
        ...  
    </assemblyBinding>  
    ```  
  
-   <span data-ttu-id="13be0-122">この問題を回避するには、接続文字列内で、"Type System Version" 属性の値を "SQL Server 2012" と指定することにより、SqlClient がバージョン 11.0 のアセンブリを読み込むようにします。</span><span class="sxs-lookup"><span data-stu-id="13be0-122">You can work around this issue in your connection string by specifying a value of "SQL Server 2012" for the "Type System Version" attribute to force SqlClient to load version 11.0 of the assembly.</span></span> <span data-ttu-id="13be0-123">この接続文字列属性は、.NET 4.5 以上でのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="13be0-123">This connection string attribute is available only in .NET 4.5 and above.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13be0-124">参照</span><span class="sxs-lookup"><span data-stu-id="13be0-124">See Also</span></span>  
 <span data-ttu-id="13be0-125">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="13be0-125">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="13be0-126">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="13be0-126">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md
)  
  
  

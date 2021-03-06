## <a name="standard-configuration-considerations"></a>標準の構成に関する考慮事項

Always On VPN には、多くの構成オプションがあります。 ただし、VPN 構成を選択すると、ただし、次の情報のとおりです。

-   **接続の種類。** 接続プロトコルの選択が重要ですし、最終的に使用する認証の種類と密接な関係が。 詳細については、利用可能なトンネリング プロトコルは、次を参照してください。 [VPN 接続の種類](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-connection-type/)します。

-   **ルーティングします。** このコンテキストでは、ルーティング規則は、ユーザーが VPN に接続されているその他のネットワーク ルートを使用できるかどうかを決定します。

    -   _分割トンネリング_インターネットなどの他のネットワークに同時にアクセスできます。

    -   _強制トンネリング_VPN のみを経由するすべてのトラフィックを必要とし、他のネットワークに同時アクセスを許可しません。

-   **トリガーします。** _トリガー_ (たとえば、アプリが開いたときに、デバイスが、ユーザーが、手動でを有効にしたとき) に VPN 接続を開始する方法とタイミングを決定します。 オプションをトリガーするには、次を参照してください。、 [VPN プロファイルの自動トリガー オプション](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile/)します。

-   **デバイスまたはユーザーの認証。** Always On VPN デバイスの証明書とデバイスが開始した接続と呼ばれる機能を使用して[デバイス トンネル](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/vpn-device-tunnel-config)します。 自動的に開始することができ、永続的で、DirectAccess インフラストラクチャ トンネル接続に似たその接続します。

>[!TIP]
>DirectAccess から Always On VPN への移行、ときに、以降を確認し、そこから順に展開に匹敵する構成オプションを検討してください。

ユーザー証明書を使用すると、Always On VPN クライアントが自動的に、接続が、ユーザー レベルで (サインイン後にユーザー) の代わりに (前のユーザー サインイン) に、、デバイス レベルで。 エクスペリエンスがユーザーに引き続きシームレスには、Windows こんにちは for Business などのより高度な認証メカニズムをサポートしています。
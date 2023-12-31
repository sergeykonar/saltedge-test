# Salt Edge SDK library changelog

## [3.5.0] - 2023-03-30

### Removed

- Removed SSL Pinning;

## [3.4.0] - 2021-02-01
### Add
- Add SEConnectHelper, CustomTabsHelper
### Changed
- update target sdk up to 30

## [3.3.0] - 2020-06-11
### Changed
- update debiancerts, update target sdk up to 29

## [3.2.0] - 2019-10-24
### Removed
- Removed Partners API v1 support;

## [3.1.0] - 2019-09-18
### Added
- Added Create OAuth provider connection
- Added Authorize OAuth provider connection

### Changed
- Moved returnToUrl initialization to SDK init
- Changed in WebViewRedirectListener onConnectSessionRedirectToReturnUrl() to onRedirectToReturnUrl(String url)

## [3.0.3] - 2019-08-06
### Added
- Added Revoke Partner Consent feature

### Changed
- Fixed Saltbridge object parse error
  
## [3.0.2] - 2019-08-05
### Added
- Added documented sources to maven repository
  
## [3.0.0] - 2019-08-01
### Added
- Added Partners API v1 support;
- Added Duplicated transactions actions:
  * fetchDuplicatedTransactionsOfAccount(...);
  * markTransactionsAsDuplicated(...);
  * markTransactionsAsNotDuplicated(...);
  * removeTransactions(...).

### Changed
- modified SEWebViewTools.WebViewRedirectListener;
- Updated documentation.
  
## [2.0.2] - 2019-07-31
### Changed
- Have been changed some dependencies declaration from `implementation` to `api` type in the `build.gradle` of the `saltedge-library`
- Updated README.md

### Added
- `transitive = true` property for `saltedge-library` dependency declaration in the `build-gradle` of the `app` module

## [2.0.1] - 2019-07-18
### Changed
- Updated a few dependencies
- Updated error message format

## [2.0.0] - 2019-04-01
### Added
- Added prefix `SE` to all base models (e.g. `SEProvider`, `SEConnection`, `SEAccount`, `SETransaction`, `SEStage`, `SEAttempt`, `SEApiError`)
- Added `Saltbridge` class
- Added `returnUrl` and `locale` to `SEAttempt`
- Added definition Consent (class `SEConsent`)
- Added SERequestManager.fetchConsents(String customerSecret, String connectionSecret, FetchConsentsResult callback)
- Added SERequestManager.revokeConsent(String customerSecret, String connectionSecret, String consentId, DeleteEntryResult callback)

### Changed
- Upgraded library to use Saltedge API v5
- Renamed all occurrences of definition `Login` to `Connection`
- Renamed all occurrences of definition `Token` to `Connect Session`
- Modified SERequestManager methods:
  * `createToken(String providerCode, String[] scopes, String returnTo, String customerSecret, TokenConnectionResult callback)` 
    to `createConnectSession(String customerSecret, String providerCode, String[] consentScopes, String localeCode, String returnToUrl, ConnectSessionResult callback)`
  * `createToken(Map<String, Object> dataMap, String customerSecret, TokenConnectionResult callback)` 
    to `createConnectSession(String customerSecret, Map<String, Object> dataMap, ConnectSessionResult callback)`
  * `reconnectToken(String localeCode, String returnTo, String loginSecret, String customerSecret, TokenConnectionResult callback)` 
    to `createReconnectSession(String customerSecret, String connectionSecret, String[] consentScopes, String localeCode, String returnToUrl, ConnectSessionResult callback)`
  * `reconnectToken(String localeCode, String returnTo, String loginSecret, String customerSecret, boolean overrideCredentials, TokenConnectionResult callback)` 
    to `createReconnectSession(String customerSecret, String connectionSecret, String[] consentScopes, String localeCode, String returnToUrl, boolean overrideCredentials, ConnectSessionResult callback)`
  * `refreshToken(String localeCode, String returnTo, String loginSecret, String customerSecret, TokenConnectionResult callback)` 
    to `createRefreshSession(String customerSecret, String connectionSecret, String localeCode, String returnToUrl, ConnectSessionResult callback)`
  * `refreshLoginWithSecret(tring customerSecret, LoginData loginData, String[] refreshScopes, RefreshLoginResult callback)` 
    to `refreshConnectionWithSecret(String customerSecret, SEConnection connectionData, String[] refreshScopes, RefreshConnectionResult callback)`
  * `fetchLogin(String customerSecret, String loginSecret, FetchLoginsResult callback)` 
    to `fetchConnection(String customerSecret, String connectionSecret, FetchConnectionsResult callback)`
  * `fetchLogin(String customerSecret, String[] loginSecretsArray, FetchLoginsResult callback)` 
    to `fetchConnection(String customerSecret, String[] connectionsSecretsArray, FetchConnectionsResult callback)`
  * `deleteLogin(String customerSecret, String loginSecret, DeleteLoginResult callback)` 
    to `deleteConnection(String customerSecret, String connectionSecret, DeleteEntryResult callback)`
  * `fetchAccounts(String customerSecret, String loginSecret, FetchAccountsResult callback)` 
    to `fetchAccounts(String customerSecret, String connectionSecret, FetchAccountsResult callback)`
  * `fetchAllTransactions(String customerSecret, String loginSecret, String accountId, FetchTransactionsResult callback)` 
    to `fetchAllTransactions(String customerSecret, String connectionSecret, String accountId, FetchTransactionsResult callback)`
  * `fetchAllTransactions(String customerSecret, String loginSecret, String accountId, String fromTransactionId, FetchTransactionsResult callback)` 
    to `fetchAllTransactions(String customerSecret, String connectionSecret, String accountId, String fromTransactionId, FetchTransactionsResult callback)`
  * `fetchTransactions(String customerSecret, String loginSecret, String accountId, String fromTransactionId, FetchTransactionsResult callback)` 
    to `fetchTransactions(String customerSecret, String connectionSecret, String accountId, String fromTransactionId, FetchTransactionsResult callback)`
  * `fetchTransactions(String customerSecret, String loginSecret, String accountId, String fromTransactionId, boolean fetchPendingTransactions, boolean fetchAllTransactionsFromId, FetchTransactionsResult callback)` 
    to `fetchTransactions(String customerSecret, String connectionSecret, String accountId, String fromTransactionId, boolean fetchPendingTransactions, boolean fetchAllTransactionsFromId, FetchTransactionsResult callback)`
  * `fetchPendingTransactionsOfAccount(String customerSecret, String loginSecret, String accountId, FetchTransactionsResult callback)` 
    to `fetchPendingTransactionsOfAccount(String customerSecret, String connectionSecret, String accountId, FetchTransactionsResult callback)`
  
- Modified WebViewRedirectListener methods:
  * `onLoginSecretFetchSuccess(String statusResponse, String loginId, String loginSecret)` 
    to `onConnectSessionSuccess(String connectionId, String connectionSecret, String stage)`
  * `onLoginSecretFetchError(String statusResponse)` 
    to `onConnectSessionError(String stage)`
  * `onLoginRefreshSuccess()` to `onConnectionUpdate()`
  * `onLoginFetchingStage(String loginId, String loginSecret)` 
    to `onConnectSessionStageChange(String connectionId, String connectionSecret, String stage, String apiStage)`.

### Removed
- CreateTokenRequest model
- SERequestManager.fetchTransactionsOfAccount
  
## [1.3.10] - 2019-03-18
### Changed
- Refactored TLSFactory

## [1.3.5] - 2018-12-10
### Added
- Network logging option

## [1.3.4] - 2018-12-05
### Changed
- Android target version to SDK 28

## [1.3.2] - 2018-09-27
### Added
- Local maven repository

## [1.2] - 2018-07-18
### Added
- SSLSocketFactory
- HPKP protocol support

## [1.1] - 2018-02-01
### Changed
- Upgrade to Saltedge API v4
- Android target version up to SDK 27
- Replaces Android Asynchronous Http Client library with Retrofit library;

## [1.0] - 2016-02-16
Upgrade to Saltedge API v3

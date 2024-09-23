# Localize

* [Localize.Find](https://hake.me/docs/systems/localize#localize-find-token)

---

## `Localize.Find(token)`​

### Arguments

* ​`token`​ - A string, e.g. `"DOTA_Chat_SentryWardBad"`​

  * Possible tokens can be found in the Dota 2 VPK in `<dota 2 folder>/pak01_dir.vpk/resource/localization`​

### Returns

A localized string for `token`​ using the current language set by Dota.

```
-- If language is set to English
Localize.Find("DOTA_Chat_SentryWardBad") == "The Dire has destroyed a Sentry Ward!"
-- If language is set to Russian
Localize.Find("DOTA_Chat_SentryWardBad") == "Силы Тьмы уничтожают Sentry Ward!"
--- etc...
```

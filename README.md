# GitHub limits

A collection of various string/numeric limits with GitHub. Not all of these are publicly documented, but I'd like to change that.

*Note: these do **not** include things like [GraphQL resource limits](https://developer.github.com/v4/guides/resource-limitations/), [REST rate limits](https://developer.github.com/v3/rate_limit/) and [disk quotas](https://help.github.com/articles/what-is-my-disk-quota/), things that are about resource usage, rather than simple strings or numbers.*

> If you're wondering why the commit history is sparse, it *is* actively maintained, but I mainly rely on others filing [issues and pull requests](#contributing). If you learn something, please, by all means, reach out!

## List of limits

Each limit carries the full set of relevant restrictions, as well as where I gained the information from.

#### Usernames

- Max length: 39 characters
- All characters must be either a hyphen (`-`) or alphanumeric
- Cannot start with a hyphen
- Cannot include consecutive hyphens
- Cannot be [a reserved name](https://github.com/Mottie/github-reserved-names)
- Must be globally unique

*This was verified through checking validation messages when attempting to create an account.*

#### Organization names

- Max length: 39 characters
- All characters must be either a hyphen (`-`) or alphanumeric
- Cannot start with a hyphen
- Cannot include consecutive hyphens
- Cannot be [a reserved name](https://github.com/Mottie/github-reserved-names)
- Must be globally unique

*This was verified through checking validation messages when attempting to create an organization.*

#### Team names

- Max length: 255 characters
- All characters must be either a hyphen (`-`) or alphanumeric
- Must be unique per-organization

Note: longer team names will still validate, they will just be truncated.

*This was verified through a support email.*

#### Profile names

- Max length: 255 characters

Note: leading/trailing whitespace will still validate, they will just be trimmed on the profile page.

*This was verified through checking validation messages and input when attempting to change the profile name.*

#### Profile bios

- Max length: 160 characters

Note: leading/trailing whitespace will still validate, they will just be trimmed on the profile page.

*This was verified through checking validation messages and input when attempting to change the profile bio.*

#### Profile URLs

- Max length: 255 characters

Note: leading/trailing whitespace will still validate, they will just be trimmed on the profile page.

*This was verified through checking validation messages and input when attempting to change the profile URL.*

#### Profile companies

- Max length: 255 characters

Note: leading/trailing whitespace will still validate, they will just be trimmed on the profile page.

*This was verified through checking validation messages and input when attempting to change the profile company.*

#### Profile locations

- Max length: 255 characters

Note: leading/trailing whitespace will still validate, they will just be trimmed.

*This was verified through checking validation messages and input when attempting to change the profile location.*

#### Repository names

- Max length: 100 code points
- All code points must be either a hyphen (`-`), an underscore (`_`), a period (`.`), or an ASCII alphanumeric code point
- Can not end with `.git`
- Must be unique per-user and/or per-organization
- The repository names containing only a single period (`.`) or double period (`..`) are reserved

Note: sequences of invalid code points are automatically replaced by a single hyphen (`-`)
Note: `.git` suffixes are automatically removed (replaced by an empty string)
Note: length checking is performed after replacement

*This was verified through checking automatically-generated aliases with repository names.*

#### Issue/pull request numbers

- Max value: 1073741824 (max 4-byte Ruby integer)
- Min value: 1

*The first was verified through a support email. The second was verified by creating an issue in an empty repo.*

#### Issue title

- Min length: 1 character
- Max length: 256 characters

*The first verified by creating an issue with a very long title and confirmed with an error message.*


#### Issue description

- Min length: 1 character
- Max length: 65536 codepoints

*The first verified by creating an issue with a very long description and confirmed with an error message.*


#### PR body 

- Min length: 0 characters
- Max length: 65536 codepoints

*This was verified by making PATCH requests to `/repos/{owner}/{repo}/pulls/{pull_number}` with `"body"` in body. This was also verified by adding longer body (262,145 characters) to a PR body in UI and confirmed with the error: `There was an error posting your comment: Body is too long`.*

### Issue comments

- Min length: 1 character
- Max length: 262144 bytes (65536-262144 characters depending on UTF8-encoded size)

*This was verified by POST-ing bodies of various sizes to a dummy issue via the V3 API.*

#### List of starred items

- Maximum number of lists in starred items: 32 lists
- Maximum number of starred project per list: unknown, but over 500 starred items
- Minimum length of the description: 1 character.
- Maximum length for a list name: 32 characters.
- Minimum length of the description: 0 characters.
- Maximum length of the description: 160 characters.

*First one was verified by creating 32 lists. (Confirmed [here](https://github.com/orgs/community/discussions/8633#discussioncomment-2631870.)).*
*Second one is unknown, there are lists with at least 500 items.*
*Others can be easily checked when creating a list.*

## Contributing

If you find limits to something not listed here, please feel free to [file an issue](https://github.com/dead-claudia/github-limits/issues/new) with details about the limits. Alternatively, you could [edit this file](https://github.com/dead-claudia/github-limits/edit/master/README.md) and file a pull request. I do need three things for each entry, though:

- The entry itself.
- Any relevant constraints, including max length, permitted characters, etc.
- How you figured out the relevant constraints.

Also, these are only confirmed with the public GitHub site. If there's a different set of limits for private data and/or enterprise setups, I'd love to have those.

## License

Copyright © 2024, Claudia Meadows and others. <a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.

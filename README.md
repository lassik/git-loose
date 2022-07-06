# git loose

When you commit files into a repo, git stores a copy of each file
under `.git/objects/`. Those copies are called _loose objects_.

As you accumulate many loose objects, Git automatically combines them
into _pack files_. Pack files use _delta compression_ to save space.

That works out well for most repos. But if you store large files which
compress poorly, git will waste a lot of time trying to compress them
anyway. This will result in pack files that are inefficient to use
locally and too big to push to sites like GitHub at all.

The `git loose` command suite helps you disable all of this
compression and packing.

`git loose`

Run this in any subdirectory of an existing git repo (either bare or
checkout) to unpack all packs and modify the local `git config` so
that git won't create new packs as you work on the repo.

`git loose-clone remote [local]`

Like `git clone` but makes sure the clone uses only loose objects.

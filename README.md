# Skills

Personal Agent Skills. Each skill is a self-contained folder with a `SKILL.md` file.

## Skills

| Skill | Use when | Path |
| --- | --- | --- |
| writing | Drafting, outlining, or revising a long-form technical article in my style. | [SKILL.md](skills/writing/SKILL.md) |

## Install

A plugin updates itself. [skills.sh](https://www.skills.sh/985563349/skills) copies editable files into your project, and you update them by hand. Pick one per agent, because installing both gives you every skill twice.

```bash
npx skills@latest add 985563349/skills -a <agent>  # cursor, opencode, devin, windsurf, amp, pi; omit -a to choose
```

### Updating

```bash
npx skills@latest update
```

Re-run the install command to pick up new skills.

## License

[MIT](LICENSE)

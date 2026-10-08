---
title: Report a problem — Auto Tab Grouper
permalink: /report/
---

# Report a problem or suggest an idea

Choose how you'd like to write. You can write in any language.

<div class="choices">
  <a class="choice" id="choice-form" href="https://tally.so/r/0QpXXP">
    <strong>Without an account</strong>
    <span>A short form. Leave your email if you'd like a reply.</span>
  </a>
  <a class="choice" id="choice-github" href="https://github.com/harlinskyi-k/auto-tab-grouper-support/issues/new/choose">
    <strong>On GitHub</strong>
    <span>Open an issue (a free GitHub account is needed). Others can follow and add to it.</span>
  </a>
  <a class="choice" id="choice-email" href="mailto:k.harlinskyi@gmail.com?subject=Auto%20Tab%20Grouper">
    <strong>By email</strong>
    <span>k.harlinskyi@gmail.com</span>
  </a>
</div>

<p class="details" id="details" hidden></p>

**Security vulnerabilities:** please report them privately — see the [security policy](../security/).

<style>
  .choices { display: grid; gap: 12px; margin: 24px 0; }
  .choice { display: block; padding: 16px 20px; border: 1px solid #d0d7de; border-radius: 8px; color: inherit; text-decoration: none; }
  .choice:hover { border-color: #0969da; background: #f6f8fa; text-decoration: none; }
  .choice strong { display: block; margin-bottom: 4px; color: #0969da; font-size: 1.1em; }
  .choice span { color: #57606a; }
  .details { color: #57606a; font-size: 0.9em; }
</style>

<script>
  // The extension opens this page with ?version=…&chrome=…&os=…&lang=…&context=… so nobody has to
  // look these up: they are passed on to the form (hidden fields), the GitHub issue form and the email.
  (function () {
    var params = new URLSearchParams(location.search);
    var info = {};
    ['version', 'chrome', 'os', 'lang', 'context'].forEach(function (key) {
      var value = (params.get(key) || '').slice(0, 100);
      if (value) info[key] = value;
    });
    if (!Object.keys(info).length) return;

    var form = new URL(document.getElementById('choice-form').href);
    Object.keys(info).forEach(function (key) { form.searchParams.set(key, info[key]); });
    document.getElementById('choice-form').href = form.href;

    // GitHub issue forms are prefilled by field id (see .github/ISSUE_TEMPLATE/bug.yml).
    var github = new URL('https://github.com/harlinskyi-k/auto-tab-grouper-support/issues/new');
    github.searchParams.set('template', 'bug.yml');
    if (info.version) github.searchParams.set('version', info.version);
    if (info.chrome || info.os) github.searchParams.set('chrome', [info.chrome && 'Chrome ' + info.chrome, info.os].filter(Boolean).join(', '));
    document.getElementById('choice-github').href = github.href;

    var lines = Object.keys(info).map(function (key) { return key + ': ' + info[key]; });
    document.getElementById('choice-email').href = 'mailto:k.harlinskyi@gmail.com?subject=' + encodeURIComponent('Auto Tab Grouper') +
      '&body=' + encodeURIComponent('\n\n---\n' + lines.join('\n'));

    var details = document.getElementById('details');
    details.textContent = 'Added automatically: ' + lines.join(' · ');
    details.hidden = false;
  })();
</script>

..
   Copyright (c) 2024 Digital Asset (Switzerland) GmbH and/or its affiliates. All rights reserved.
..
   SPDX-License-Identifier: Apache-2.0

.. NOTE: add your upcoming release notes below this line. They are included in the `release_notes.rst`.

.. release-notes:: Upcoming

    - SV app

        - The SV web UI can now run in an optional dApp mode for delegated
          governance voting (``dappMode`` UI config, or the
          ``SPLICE_APP_UI_DAPP_MODE_*`` variables of the ``sv-web-ui`` image):
          login through a CIP-0103 wallet, governance reads from Scan, and
          vote submissions signed by a delegated voter party via a
          ``VoteDelegation`` contract. Disabled by default; standard
          deployments are unaffected. See :ref:`sv-dapp-mode`.

    - Wallet app

        - Duplicate wallet operations submitted with the same command id (e.g. tap, transfer,
          token standard transfers) now return the original result idempotently instead of HTTP 409.
          This aligns with standard idempotency-key semantics: a second request with a previously
          accepted command id receives a 200 response with the same result as the first.
          Concurrent duplicates, where no submission has completed yet, are still rejected.

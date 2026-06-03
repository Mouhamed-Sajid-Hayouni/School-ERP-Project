# Runtime Smoke Test - final-verification-v2.80

## Checkpoint

- Final tag: final-verification-v2.80
- Root commit: a6fdf21
- Backend submodule: 9f36809
- Web submodule: 18cc132
- Mobile submodule: 9c97637

## Verification

The following checks passed before the final tag:

- Backend build passed.
- Web lint passed.
- Web build passed with only the known non-blocking Vite chunk-size warning.
- Mobile verify passed.
- Arabic encoding check passed.
- Root, backend, web and mobile repositories were clean and up to date.

## Fresh clone test

A fresh clone with recursive submodules was tested successfully. The project checked out tag final-verification-v2.80 and resolved all submodules correctly.

## Runtime smoke test

The application was tested locally with:

- Backend running on port 5000.
- Web frontend running on localhost:5173.
- Dashboard opened successfully.
- Users page opened successfully.
- Teacher absences page opened successfully.
- A teacher absence was recorded and displayed successfully.

## Notes

The local backend environment was adjusted so the PostgreSQL SSL warning no longer appears during startup.
The .env file must remain private and must not be committed.

## Final status

The project is ready for delivery from checkpoint final-verification-v2.80.

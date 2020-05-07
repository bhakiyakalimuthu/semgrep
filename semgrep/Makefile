all:
	./build.sh ./build/
clean:
	rm -rf ./build/
test:
	PYTHONPATH=. pytest tests/
regenerate-tests:
	PYTHONPATH=. pytest tests/ --snapshot-update
install:
	cp -rv ./build/semgrep.dist/ /usr/local/bin/semgrep-files/
	ln -sf /usr/local/bin/semgrep-files/semgrep /usr/local/bin/semgrep

.PHONY: qa-test
qa-test: PYTHONPATH=. pytest tests/ --qa

.PHONY: benchmark
benchmark:
	PYTHONPATH=. pytest tests/ --benchmark-only $(ARGS)

.PHONY: benchmark-snapshot
benchmark-snapshot:
	@read -p "Name your snapshot: " snapshot_name;\
	PYTHONPATH=. pytest tests/ --benchmark-only --benchmark-save=$$snapshot_name $(ARGS)

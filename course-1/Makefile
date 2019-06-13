#!make
#@ Makefile for Neural Networks and Deep Learning Coursera course

#@ Commands:
.PHONY: help-one init-one run-one
.DEFAULT_GOAL := help-one

SHELL := /bin/bash
CONTEXT_COURSE_1 := $(or $(CONTEXT_COURSE_1),.)

%: %-one
	@true

#@ - help: Show all commands.
help-one:
	@fgrep -h "#@ " $(MAKEFILE_LIST) | fgrep -v fgrep | sed -e 's/\\$$//' | sed -e 's/#@ //'

#@ - init: Download requirements.
init-one:
	@cd ${CONTEXT_COURSE_1}/ && \
	python3 -m venv .venv && \
	source .venv/bin/activate && \
	pip install --upgrade pip && \
	pip install -r requirements.txt

#@ - run: Run jupyter notebook.
run-one:
	@cd ${CONTEXT_COURSE_1}/ && \
	if [ ! -d ".venv" ]; then \
		${MAKE} init-one; \
	fi && \
	source .venv/bin/activate && \
	jupyter notebook --notebook-dir=.

#@ - clean: Delete venv
clean-one:
	@cd ${CONTEXT_COURSE_1}/ && \
	if [ -d ".venv" ]; then \
		trash .venv; \
	fi